---
layout: post
title: "Guava Cache with Removal Listener"
categories: java
---


```
package learning;

import com.google.common.cache.Cache;
import com.google.common.cache.CacheBuilder;
import com.google.common.cache.RemovalListener;
import com.google.common.cache.RemovalNotification;
import java.util.HashSet;
import java.util.Set;
import java.util.concurrent.TimeUnit;
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
  public void simpleTest()
      throws Exception {
    CacheBuilder<String, Boolean> builder = CacheBuilder.newBuilder()
        .expireAfterWrite(10, TimeUnit.MILLISECONDS)
        .removalListener(new SimpleRemovalListener());
    Cache<String, Boolean> cache = builder.build();
    cache.put("A123", true);
    cache.size();
    //TODO(MGP): Use the ticker thing to make a better test!!
    Thread.sleep(20L); 
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
}

```

