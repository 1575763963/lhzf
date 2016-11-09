---
title: 案件处理之后提交到后台 
tags: 案件,处理,附属
grammar_cjkRuby: true
---

> flowtasktack 表结构: 
> 
    drop table if exists flowtasktack;

    /*==============================================================*/
    /* Table: flowtasktack                                          */
    /*==============================================================*/
    create table flowtasktack
    (
       id                   char(32) not null comment '附属ID',
       fid                  char(32) not null comment '案件ID',
       csarea               int comment '乱搭建/面积',
       bgbottle             int comment '黑煤气/瓶',
       ninvers              int comment '报刊亭/排查',
       nremoved             int comment '报刊亭/调离',
       isinvers             int comment '非法办学/排查',
       isremoved            int comment '非法办学/调离',
       crtid                char(32) comment '创建人ID',
       crttm                datetime not null comment '创建时间',
       updid                char(32) comment '修改人ID',
       updtm                datetime not null comment '修改时间',
       primary key (id)
    )
    ENGINE=InnoDB DEFAULT CHARSET=utf8 ROW_FORMAT=COMPACT;

    alter table flowtasktack comment '案件附属表(flowtasktack)';

> 针对排查和调离，如果只有排查则只传入排查:1 不用传输调离
> 比如：ninvers：1

添加协作人员字段：cooperation varchar(255)
后台有判断如果值不为空则处理否则放弃

