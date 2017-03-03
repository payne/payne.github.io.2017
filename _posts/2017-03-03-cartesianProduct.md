---
layout: post
title: "cartesianProduct(a, b)"
categories: java
---


```
package learning;

import com.google.common.collect.Sets;
import java.util.*;
import org.junit.Test;

import static org.junit.Assert.*;
import static org.hamcrest.CoreMatchers.is;

public class CartesianProductTest {
  @Test
  public void test() {
    Set<String> a = new HashSet<>(Arrays.asList("a", "b", "c"));
    Set<String> b = new HashSet<>(Arrays.asList("1", "2"));
    Set<List<String>> ab = Sets.cartesianProduct(a, b);
    assertThat(ab.toString(), 
      is("[[a, 1], [a, 2], [b, 1], [b, 2], [c, 1], [c, 2]]"));
  }
}
```

