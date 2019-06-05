#### aJava-clone使用场景

##### 在写bean类的时候，变量有可能是一个引用数据类型，比如Date 

```java
public class Person {
    private Date date;
    public Date getDate() {
        return date;
    }
    public void setDate(Date date) {
        this.date = date;
    }
}
```

- 然后对这个类进行测试

  ```java
  public class CloneTest {
  
      public static void testClone(){
          Person person = new Person();
          person.setDate(new Date());
          System.out.println("before"+person.getDate());
  
          Date getDate = person.getDate();
          getDate.setTime(1111111111);
          System.out.println("after"+person.getDate());
          System.out.println("getDate = " + getDate);
      }
  
      public static void main(String[] args) {
          testClone();
      }
  
  }
  ```

- 运行输出

  ```java
  beforeSun May 05 11:54:31 CST 2019
  afterWed Jan 14 04:38:31 CST 1970
  getDate = Wed Jan 14 04:38:31 CST 1970
  ```

  

- 可以看到，getDate改变数据，直接导致person中的date变量也改变了

- 因为date和getDate引用的是同一个对象

