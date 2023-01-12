-- home_erp.su_user definition

CREATE TABLE `su_user` (
  `id` int NOT NULL AUTO_INCREMENT,
  `login_name` varchar(20) NOT NULL COMMENT '登录账号',
  `login_pwd` varchar(50) NOT NULL COMMENT 'SHA1加密之后的密码',
  `name` varchar(100) NOT NULL COMMENT '用户的真实名字',
  `title` varchar(100) DEFAULT NULL COMMENT '职位名称',
  `department` varchar(100) DEFAULT NULL COMMENT '所属部门',
  `contact` varchar(100) DEFAULT NULL COMMENT '联系方式',
  `status` char(1) DEFAULT '0' COMMENT '当前状态：\r\n0 正常\r\n1 已删除\r\n2 禁用',
  `comment` varchar(100) DEFAULT NULL COMMENT '备注信息',
  `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`id`),
  KEY `su_user_login_name_IDX` (`login_name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='用户表';


-- home_erp.su_vip definition

CREATE TABLE `su_vip` (
  `id` int NOT NULL AUTO_INCREMENT,
  `vip_id` varchar(10) NOT NULL COMMENT '会员编号',
  `name` varchar(100) NOT NULL COMMENT '会员名称',
  `contact` varchar(100) DEFAULT NULL COMMENT '联系方式',
  `address` varchar(300) DEFAULT NULL COMMENT '地址',
  `total_amount` int NOT NULL DEFAULT '0' COMMENT '总消费金额',
  `vip_level` int DEFAULT NULL COMMENT '消费等级',
  `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`id`),
  KEY `su_vip_vip_id_IDX` (`vip_id`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='会员信息表';


-- home_erp.su_vip_level definition

CREATE TABLE `su_vip_level` (
  `id` int NOT NULL AUTO_INCREMENT,
  `level_name` varchar(10) NOT NULL COMMENT '等级显示名称',
  `cost_amount` int NOT NULL DEFAULT '0' COMMENT '消费限额',
  `comment` int DEFAULT NULL COMMENT '备注',
  PRIMARY KEY (`id`),
  KEY `su_vip_level_level_name_IDX` (`level_name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='会员等级表';


-- home_erp.su_supplier definition
CREATE TABLE `su_supplier` (
  `id` int(20) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `supplier` varchar(255) NOT NULL COMMENT '供应商名称',
  `contact_name` varchar(100) DEFAULT NULL COMMENT '联系人',
  `contact` varchar(30) DEFAULT NULL COMMENT '联系电话',
  `email` varchar(50) DEFAULT NULL COMMENT '电子邮箱',
  `create_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime DEFAULT CURRENT_TIMESTAMP COMMENT '更新时间',
  `comment` varchar(500) DEFAULT NULL COMMENT '备注',
  `status_flag` varchar(1) DEFAULT '0' COMMENT '0 正常, 1 拉黑',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='供应商/客户信息表';



-- home_erp.su_material_category definition
CREATE TABLE `su_material_category` (
  `id` int(20) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `name` varchar(50) DEFAULT NULL COMMENT '名称',
  `category_level` smallint(6) DEFAULT NULL COMMENT '等级',
  `parent_id` int(20) DEFAULT NULL COMMENT '上级id',
  `sort` varchar(10) DEFAULT NULL COMMENT '显示顺序',
  `serial_no` varchar(100) DEFAULT NULL COMMENT '编号',
  `comment` varchar(1024) DEFAULT NULL COMMENT '备注',
  `create_time` timestamp DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` timestamp DEFAULT CURRENT_TIMESTAMP COMMENT '更新时间',
  `delete_flag` varchar(1) DEFAULT '0' COMMENT '删除标记，0未删除，1删除',
  PRIMARY KEY (`id`),
  KEY `su_material_category_parent_id_IDX` (`parent_id`)
) ENGINE=InnoDB AUTO_INCREMENT=29 DEFAULT CHARSET=utf8 COMMENT='产品类型表';

