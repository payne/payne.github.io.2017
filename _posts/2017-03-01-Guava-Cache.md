---
layout: post
title: "Guava Cache with Removal Listener"
categories: java
---


```
package learning;

import com.google.common.base.Ticker;
import com.google.common.cache.Cache;
import com.google.common.cache.CacheBuilder;
import com.google.common.cache.RemovalListener;
import com.google.common.cache.RemovalNotification;
import java.util.HashSet;
import java.util.Set;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.atomic.AtomicLong;
import org.junit.Before;
import org.junit.Test;

import static org.hamcrest.CoreMatchers.is;
import static org.junit.Assert.assertThat;


public class CacheTests {
  final Set<String> removed = new HashSet<>();

  @Before
  public void setup() {
    removed.clear();
  }

  @Test
  public void simpleTest() throws Exception {
    FakeTicker t = new FakeTicker();
    CacheBuilder<String, Boolean> builder = CacheBuilder.newBuilder().expireAfterWrite(10, TimeUnit.MILLISECONDS)
        .removalListener(new SimpleRemovalListener()).ticker(t);
    Cache<String, Boolean> cache = builder.build();
    cache.put("A123", true);
    cache.size();
    t.advance(11, TimeUnit.MILLISECONDS);
    cache.put("A124", true);
    cache.put("A125", true);
    assertThat(removed.size(), is(1));
  }

  class SimpleRemovalListener implements RemovalListener {

    @Override
    public void onRemoval(RemovalNotification notification) {
      System.out.println("onRemoval notification=" + notification);
      removed.add((String) notification.getKey());
    }
  }

  // http://stackoverflow.com/questions/29990788/guava-ticker-cache-expire
  class FakeTicker extends Ticker {

    private final AtomicLong nanos = new AtomicLong();

    /** Advances the ticker value by {@code time} in {@code timeUnit}. */
    public FakeTicker advance(long time, TimeUnit timeUnit) {
      nanos.addAndGet(timeUnit.toNanos(time));
      return this;
    }

    @Override
    public long read() {
      long value = nanos.getAndAdd(0);
      System.out.println("is called " + value);
      return value;
    }
  }

}
```

