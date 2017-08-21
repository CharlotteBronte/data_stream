
data\_stream --ai数据更新线下流程
====
# 功能介绍
  定期从线上拉取全量数据文件,并同步到mysql中，计算出diff  
   ![image](https://github.com/pangdaxing/data_stream.git/raw/master/images/数据流_new.png)
# useage:
  bash runner.sh module\_name cmd\_name
  eg:sh runner.sh decode diff\_num

# 目录说明
  * runner--不同模块的执行命令
    * decode:
        * get_diff: 得到decode各个产品线的diff放到流程中
        * diff_num: 得到产品线的diff数量,超过限制了就发邮件
        * load_base: 将当前的all覆盖base
  * script--分目录存放了各个模块的所有的更新流程可执行脚本
     * decode:tag_decode的数据流
        * es_stream: 从esdump文件并拿到本地构建txt文件
        * mysql_stream: 从本地txt文件导入mysql，执行diff计算

  * config--存放所有配置信息
    * db.conf:目前的所有模块的相关配置
  * data--存放所有中间结果文件
    * decode
        * mysqldata: 需要导入到数据库的所有data
        * finaldata: decode的最终词典目录
        * origindata:从es更新下来的词典目录
  * log--天级更新的日志文件
