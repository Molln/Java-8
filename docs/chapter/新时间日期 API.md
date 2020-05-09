# 新时间日期 API

### 一 传统日期时间 API

传统日期时间格式化存在线程安全问题

### 二 本地时间

LocalDate

LocalTime

LocalDateTime

LocalDate、LocalTime、LocalDateTime 类的实例时**不可变的对象**，分别表示使用 ISO-8601 日历系统的日期、时间、日期时间。它们提供了简单的日期或时间，并不包含当前的时间信息。也不包含与时区相关的信息。

注：ISO-8601 日历系统是国际标准化组织制定的现代公民的日期和时间的表示法。

![](img/LocalDateTime.jpg)

### 三 时间戳

`Instant` 用于”时间戳“的运算。他是以 Unix 元年开始所经历的描述进行运算。

Unix 元年：UTC 时区 1970 年 1 月 1 日 0 点 0 分 0 秒 

Duration	用于计算两个”时间“间隔

Period		用于计算两个”日期“间隔

### 四 时间校正器

TemporalAdjuster     时间矫正器。有时我们可能需要获取例如：下周日的日期

TemporalAdjusters   该类通过静态方法提供了大量的常用 TemporalAdjuster 实现。

示例：获取下周日

````java
LocalDate nextSunday = LocalDate.now().with(
    TemporalAdjusters.next(DayOfWeek.SUNDAY)
);
````

### 五 时间格式化

`java.time.format.DateTimeFormatter`

三种格式化方法：

* 预定义的标准格式
* 语言环境相关的格式
* 自定义的格式

### 六 时区

Java 8 中加入了对时区的支持，带时区的日期时间分别为 ZonedDate、ZonedTime、ZonedDateTime

每个时区都有对应的 ID，时区 ID 格式为 “{区域}/{城市}”，例如：Asia/Shanghai

ZoneId.class	该类中包含了所有的时区信息

* getAvailableZoneIds()    获取所有支持的时区
* of(id)    根据时区Id 获取 ZoneId 对象

### 七 与传统日期时间的转换

![](img/OldNew.jpg)