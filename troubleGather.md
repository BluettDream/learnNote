##### Lombok

提示Module lombok not found，出现Error occurred during initialization of boot layer；java.lang.module.FindException: Module lombok not found, required by ...

解决办法：module-info里加入：requires **static** lombok;