# next_day

## 功能

根据输入的日期值，返回它之后的那个星期几所对应的日期。比如 `next_day('2023-04-06', 'Monday')` 返回 '2023-04-06' 之后的那个星期一所对应的日期。

该函数从 3.1 版本开始支持。相反函数为 [previous_day](./previous_day.md)。

## 语法

```SQL
DATE next_day(DATETIME|DATE date_expr, VARCHAR dow)
```

## 参数说明

- `date_expr`：输入的日期值，支持的数据类型为 DATE 或 DATETIME。
- `dow`：星期几。有效值为星期和以下缩写形式，区分大小写。
  
  | DOW_FULL  | DOW_2 | DOW_3 |
  | --------- | ----- |:-----:|
  | Sunday    | Su    | Sun   |
  | Monday    | Mo    | Mon   |
  | Tuesday   | Tu    | Tue   |
  | Wednesday | We    | Wed   |
  | Thursday  | Th    | Thu   |
  | Friday    | Fr    | Fri   |
  | Saturday  | Sa    | Sat   |

## 返回值说明

返回一个日期值。

如果 `dow` 输入值非法，会返回报错。`dow` 区分大小写。

如果输入的日期值非法或者输入的日期为 NULL，则返回 NULL。

## 示例

```Plain
-- 返回 2023-04-06 之后的那个星期一所对应的日期。2023-04-06 为周四，它之后的星期一所对应的日期为 2023-04-10。

MySQL > select next_day('2023-04-06', 'Monday');
+----------------------------------+
| next_day('2023-04-06', 'Monday') |
+----------------------------------+
| 2023-04-10                       |
+----------------------------------+

MySQL > select next_day('2023-04-06', 'Tue');
+-------------------------------+
| next_day('2023-04-06', 'Tue') |
+-------------------------------+
| 2023-04-11                    |
+-------------------------------+

MySQL > select next_day('2023-04-06 20:13:14', 'Fr');
+---------------------------------------+
| next_day('2023-04-06 20:13:14', 'Fr') |
+---------------------------------------+
| 2023-04-07                            |
+---------------------------------------+
```

## keyword

NEXT_DAY, NEXT
