## 1. [EishayFuryCompatibleParse](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayFuryCompatibleParse.java)
这个场景是JSONB格式和Fury CompatibleMode反序列化性能比较。基于KeyValue的映射，对增加和删除字段的序列化结构都能有很好的兼容性。

| aliyun ecs spec | jdk version 	|	jsonb	|	fury |
|-----|-----|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	6893.827	|	6944.665 (100.74%) |
|  | jdk-11.0.20	|	7928.25	|	7057.197 (89.01%) |
|  | jdk-17.0.8	|	8609.988	|	9472.562 (110.02%) |
|  | jdk-21.0.2	|	8721.716	|	9280.756 (106.41%) |
|  | jdk-24	|	9208.18	|	9794.182 (106.36%) |
|  | graalvm_24+36.1	|	13355.369	|	11812.828 (88.45%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	8177.937	|	9028.157 (110.4%) |
|  | jdk-11.0.20	|	9106.706	|	9453.267 (103.81%) |
|  | zulu17.54.21	|	9464.632	|	9710.713 (102.6%) |
|  | jdk-21.0.2	|	10087.834	|	10268.787 (101.79%) |
|  | jdk-24	|	11088.337	|	9674.634 (87.25%) |
|  | graalvm_24+36.1	|	13342.253	|	11781.186 (88.3%) |
| MacBookM1Pro | zulu-8.jdk	|	26556.051	|	19241.904 (72.46%) |
|  | zulu-11.jdk	|	18591.068	|	19113.683 (102.81%) |
|  | zulu-17.jdk	|	29670.851	|	32355.498 (109.05%) |
|  | zulu-21.jdk	|	29587.125	|	32396.531 (109.5%) |
|  | jdk-24.jdk	|	30491.395	|	31149.114 (102.16%) |
|  | graalvm_24+36.1	|	44081.806	|	46989.298 (106.6%) |

## 2. [EishayFuryCompatibleWrite](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayFuryCompatibleWrite.java)
这个场景是JSONB格式和Fury CompatibleMode序列化性能比较。基于KeyValue的映射，对增加和删除字段的序列化结构都能有很好的兼容性。

| aliyun ecs spec | jdk version 	|	jsonb	|	fury |
|-----|-----|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	8731.904	|	6715.727 (76.91%) |
|  | jdk-11.0.20	|	9724.037	|	8374.195 (86.12%) |
|  | jdk-17.0.8	|	11314.494	|	10057.986 (88.89%) |
|  | jdk-21.0.2	|	11799.486	|	9113.843 (77.24%) |
|  | jdk-24	|	11482.571	|	8493.426 (73.97%) |
|  | graalvm_24+36.1	|	10259.051	|	7484.184 (72.95%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	8976.289	|	8176.93 (91.09%) |
|  | jdk-11.0.20	|	10107.684	|	9285.235 (91.86%) |
|  | zulu17.54.21	|	10448.987	|	9681.162 (92.65%) |
|  | jdk-21.0.2	|	10936.278	|	7827.75 (71.58%) |
|  | jdk-24	|	11189.809	|	8809.508 (78.73%) |
|  | graalvm_24+36.1	|	12172.092	|	8415.996 (69.14%) |
| MacBookM1Pro | zulu-8.jdk	|	29848.617	|	8715.66 (29.2%) |
|  | zulu-11.jdk	|	21454.819	|	11805.755 (55.03%) |
|  | zulu-17.jdk	|	40802.314	|	14625.155 (35.84%) |
|  | zulu-21.jdk	|	37383.957	|	18725.472 (50.09%) |
|  | jdk-24.jdk	|	33921.734	|	16908.1 (49.84%) |
|  | graalvm_24+36.1	|	28486.76	|	15944.905 (55.97%) |

## 3. [EishayParseBinary](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseBinary.java)
这个场景是二进制反序列化比较，JSONB格式、JSON UTF8编码(fastjson2UTF8Bytes)、hessian、javaSerialize的比较，用于[Apache dubbo](https://github.com/apache/dubbo)的用户选择二进制协议比较

| aliyun ecs spec | jdk version 	|	jsonb	|	fastjson2UTF8Bytes	|	hessian	|	javaSerialize |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	8241.926	|	3770.217 (45.74%)	|	836.976 (10.16%)	|	141.098 (1.71%) |
|  | jdk-11.0.20	|	9231.547	|	4690.738 (50.81%)	|	758.09 (8.21%)	|	149.047 (1.61%) |
|  | jdk-17.0.8	|	10034.456	|	6042.621 (60.22%)	|	783.278 (7.81%)	|	168.064 (1.67%) |
|  | jdk-21.0.2	|	10491.775	|	5988.366 (57.08%)	|	807.911 (7.7%)	|	156.003 (1.49%) |
|  | jdk-24	|	10550.165	|	6142.615 (58.22%)	|	854.765 (8.1%)	|	154.751 (1.47%) |
|  | graalvm_24+36.1	|	15540.602	|	8598.883 (55.33%)	|	942.158 (6.06%)	|	156.498 (1.01%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	9292.065	|	5353.285 (57.61%)	|	457.842 (4.93%)	|	180.08 (1.94%) |
|  | jdk-11.0.20	|	10082.867	|	5947.588 (58.99%)	|	478.604 (4.75%)	|	174.187 (1.73%) |
|  | zulu17.54.21	|	10708.254	|	6316.382 (58.99%)	|	596.193 (5.57%)	|	172.036 (1.61%) |
|  | jdk-21.0.2	|	11166.717	|	6590.662 (59.02%)	|	582.155 (5.21%)	|	177.75 (1.59%) |
|  | jdk-24	|	12788.466	|	7031.009 (54.98%)	|	998.673 (7.81%)	|	187.649 (1.47%) |
|  | graalvm_24+36.1	|	15513.699	|	7311.076 (47.13%)	|	727.99 (4.69%)	|	190.482 (1.23%) |
| MacBookM1Pro | zulu-8.jdk	|	39178.491	|	18188.274 (46.42%)	|	898.821 (2.29%)	|	446.167 (1.14%) |
|  | zulu-11.jdk	|	18619.903	|	14584.373 (78.33%)	|	606.04 (3.25%)	|	305.969 (1.64%) |
|  | zulu-17.jdk	|	44233.911	|	20437.814 (46.2%)	|	754.219 (1.71%)	|	539.942 (1.22%) |
|  | zulu-21.jdk	|	43613.993	|	20881.038 (47.88%)	|	808.311 (1.85%)	|	518.903 (1.19%) |
|  | jdk-24.jdk	|	42735.862	|	20319.116 (47.55%)	|	882.934 (2.07%)	|	590.423 (1.38%) |
|  | graalvm_24+36.1	|	58752.612	|	30100.464 (51.23%)	|	1057.113 (1.8%)	|	576.738 (0.98%) |

## 4. [EishayParseBinaryArrayMapping](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseBinaryArrayMapping.java)
这个场景是二进制反序列化比较，JSONB格式（基于字段顺序映射）、kryo、protobuf的比较

| aliyun ecs spec | jdk version 	|	jsonb	|	kryo	|	protobuf |
|-----|-----|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	9388.047	|	4549.32 (48.46%)	|	3977.977 (42.37%) |
|  | jdk-11.0.20	|	13075.221	|	4388.297 (33.56%)	|	4394.051 (33.61%) |
|  | jdk-17.0.8	|	14449.717	|	4656.74 (32.23%)	|	5964.595 (41.28%) |
|  | jdk-21.0.2	|	14807.527	|	4888.943 (33.02%)	|	5725.164 (38.66%) |
|  | jdk-24	|	15284.719	|	5060.198 (33.11%)	|	6057.829 (39.63%) |
|  | graalvm_24+36.1	|	22077.14	|	5125.697 (23.22%)	|	8225.102 (37.26%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	12575.356	|	6083.729 (48.38%)	|	3992.559 (31.75%) |
|  | jdk-11.0.20	|	12661.273	|	5192.738 (41.01%)	|	3602.723 (28.45%) |
|  | zulu17.54.21	|	11809.696	|	5389.138 (45.63%)	|	5406.333 (45.78%) |
|  | jdk-21.0.2	|	14124.585	|	5918.306 (41.9%)	|	6310.699 (44.68%) |
|  | jdk-24	|	17955.693	|	6184.863 (34.45%)	|	6897.151 (38.41%) |
|  | graalvm_24+36.1	|	23527.474	|	5719.381 (24.31%)	|	8681.771 (36.9%) |
| MacBookM1Pro | zulu-8.jdk	|	50312.682	|	13087.295 (26.01%)	|	11844.045 (23.54%) |
|  | zulu-11.jdk	|	37197.955	|	10816.805 (29.08%)	|	8996.514 (24.19%) |
|  | zulu-17.jdk	|	52694.56	|	15058.413 (28.58%)	|	18173.845 (34.49%) |
|  | zulu-21.jdk	|	57903.942	|	11833.176 (20.44%)	|	16393.813 (28.31%) |
|  | jdk-24.jdk	|	59630.353	|	14718.629 (24.68%)	|	16561.455 (27.77%) |
|  | graalvm_24+36.1	|	86961.38	|	17147.965 (19.72%)	|	33646.989 (38.69%) |

## 5. [EishayParseBinaryAutoType](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseBinaryAutoType.java)
这个场景是带类型信息二进制反序列化比较，JSONB格式、JSON UTF8编码(fastjson2UTF8Bytes)、hessian、javaSerialize的比较，用于[Apache dubbo](https://github.com/apache/dubbo)的用户选择二进制协议比较

| aliyun ecs spec | jdk version 	|	fastjson2JSONB	|	hessian	|	javaSerialize |
|-----|-----|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	4590.367	|	835.792 (18.21%)	|	140.538 (3.06%) |
|  | jdk-11.0.20	|	5127.469	|	788.324 (15.37%)	|	146.648 (2.86%) |
|  | jdk-17.0.8	|	5177.245	|	785.61 (15.17%)	|	171.941 (3.32%) |
|  | jdk-21.0.2	|	5135.527	|	807.795 (15.73%)	|	156.096 (3.04%) |
|  | jdk-24	|	5293.709	|	854.355 (16.14%)	|	155.842 (2.94%) |
|  | graalvm_24+36.1	|	6406.066	|	959.726 (14.98%)	|	154.629 (2.41%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	5212.726	|	525.519 (10.08%)	|	174.536 (3.35%) |
|  | jdk-11.0.20	|	5810.154	|	424.915 (7.31%)	|	170.933 (2.94%) |
|  | zulu17.54.21	|	5905.09	|	612.712 (10.38%)	|	172.936 (2.93%) |
|  | jdk-21.0.2	|	5657.64	|	576.462 (10.19%)	|	177.09 (3.13%) |
|  | jdk-24	|	6092.49	|	906.809 (14.88%)	|	192.421 (3.16%) |
|  | graalvm_24+36.1	|	7132.068	|	665.874 (9.34%)	|	191.528 (2.69%) |
| MacBookM1Pro | zulu-8.jdk	|	18447.193	|	913.51 (4.95%)	|	437.884 (2.37%) |
|  | zulu-11.jdk	|	13561.242	|	608.368 (4.49%)	|	332.598 (2.45%) |
|  | zulu-17.jdk	|	20991.161	|	836.057 (3.98%)	|	539.011 (2.57%) |
|  | zulu-21.jdk	|	19551.02	|	830.401 (4.25%)	|	536.616 (2.74%) |
|  | jdk-24.jdk	|	20731.648	|	931.609 (4.49%)	|	575.453 (2.78%) |
|  | graalvm_24+36.1	|	24205.448	|	1074.72 (4.44%)	|	561.026 (2.32%) |

## 6. [EishayParseString](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseString.java)
这个场景是将没有格式化的JSON字符串反序列化为JavaBean对象，是最常用的场景，这个是fastjson1的强项。

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	4387.265	|	3275.713 (74.66%)	|	1451.408 (33.08%)	|	1324.525 (30.19%) |
|  | jdk-11.0.20	|	4836.862	|	2823.945 (58.38%)	|	1348.727 (27.88%)	|	1355.523 (28.02%) |
|  | jdk-17.0.8	|	6170.011	|	4054.94 (65.72%)	|	1426.465 (23.12%)	|	1398.764 (22.67%) |
|  | jdk-21.0.2	|	6294.923	|	3976.094 (63.16%)	|	1339.302 (21.28%)	|	1222.083 (19.41%) |
|  | jdk-24	|	6119.901	|	3218.994 (52.6%)	|	1342.697 (21.94%)	|	1238.492 (20.24%) |
|  | graalvm_24+36.1	|	7585.415	|	4366.245 (57.56%)	|	1375.64 (18.14%)	|	1390.583 (18.33%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	5914.126	|	3765.305 (63.67%)	|	1609.55 (27.22%)	|	1593.614 (26.95%) |
|  | jdk-11.0.20	|	6100.019	|	3474.906 (56.97%)	|	1510.968 (24.77%)	|	1512.946 (24.8%) |
|  | zulu17.54.21	|	6455.923	|	4697.217 (72.76%)	|	1526.663 (23.65%)	|	1555.506 (24.09%) |
|  | jdk-21.0.2	|	6660.026	|	4695.571 (70.5%)	|	1497.953 (22.49%)	|	1390.653 (20.88%) |
|  | jdk-24	|	7313.523	|	4000.431 (54.7%)	|	1481.799 (20.26%)	|	1430.914 (19.57%) |
|  | graalvm_24+36.1	|	7356.257	|	4693.446 (63.8%)	|	1501.966 (20.42%)	|	1478.837 (20.1%) |
| MacBookM1Pro | zulu-8.jdk	|	21776.99	|	11703.275 (53.74%)	|	4820.074 (22.13%)	|	5417.694 (24.88%) |
|  | zulu-11.jdk	|	14488.158	|	7388.995 (51%)	|	3324.275 (22.94%)	|	3894.683 (26.88%) |
|  | zulu-17.jdk	|	20825.274	|	16393.531 (78.72%)	|	4571.576 (21.95%)	|	5620.2 (26.99%) |
|  | zulu-21.jdk	|	20076.297	|	15750.988 (78.46%)	|	4745.417 (23.64%)	|	5400.41 (26.9%) |
|  | jdk-24.jdk	|	20347.11	|	11879.338 (58.38%)	|	5113.484 (25.13%)	|	5421.565 (26.65%) |
|  | graalvm_24+36.1	|	30199.272	|	14057.695 (46.55%)	|	4854.649 (16.08%)	|	4971.888 (16.46%) |

## 7. [EishayParseStringPretty](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseStringPretty.java)
这个场景是将格式化过的JSON字符串反序列化为JavaBean对象

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	3593.094	|	887.942 (24.71%)	|	1332.714 (37.09%)	|	1217.027 (33.87%) |
|  | jdk-11.0.20	|	3614.26	|	763.11 (21.11%)	|	1264.783 (34.99%)	|	1257.052 (34.78%) |
|  | jdk-17.0.8	|	4369.592	|	953.477 (21.82%)	|	1271.642 (29.1%)	|	1269.904 (29.06%) |
|  | jdk-21.0.2	|	4343.032	|	907.004 (20.88%)	|	1257.806 (28.96%)	|	1133.367 (26.1%) |
|  | jdk-24	|	4536.867	|	828.276 (18.26%)	|	1189.679 (26.22%)	|	1194.403 (26.33%) |
|  | graalvm_24+36.1	|	4445.6	|	1110.866 (24.99%)	|	1248.354 (28.08%)	|	1175.748 (26.45%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	4209.586	|	1036.289 (24.62%)	|	1457.449 (34.62%)	|	1465.953 (34.82%) |
|  | jdk-11.0.20	|	3079.079	|	1038.377 (33.72%)	|	1366.732 (44.39%)	|	1364.644 (44.32%) |
|  | zulu17.54.21	|	4564.258	|	1137.432 (24.92%)	|	1452.603 (31.83%)	|	1487.485 (32.59%) |
|  | jdk-21.0.2	|	4738.331	|	1039.564 (21.94%)	|	1386.05 (29.25%)	|	1249.052 (26.36%) |
|  | jdk-24	|	5060.092	|	963.549 (19.04%)	|	1418.197 (28.03%)	|	1395.111 (27.57%) |
|  | graalvm_24+36.1	|	4992.913	|	1270.252 (25.44%)	|	1367.12 (27.38%)	|	1411.216 (28.26%) |
| MacBookM1Pro | zulu-8.jdk	|	14428.664	|	3457.762 (23.96%)	|	4713.875 (32.67%)	|	5041.853 (34.94%) |
|  | zulu-11.jdk	|	9621.944	|	1919.64 (19.95%)	|	3044.885 (31.65%)	|	3345.105 (34.77%) |
|  | zulu-17.jdk	|	15616.315	|	3010.26 (19.28%)	|	4443.917 (28.46%)	|	5202.37 (33.31%) |
|  | zulu-21.jdk	|	15300.963	|	3595.976 (23.5%)	|	4585.441 (29.97%)	|	4912.064 (32.1%) |
|  | jdk-24.jdk	|	15694.669	|	3249.205 (20.7%)	|	4471.887 (28.49%)	|	5063.643 (32.26%) |
|  | graalvm_24+36.1	|	2478.515	|	4352.105 (175.59%)	|	4503.013 (181.68%)	|	4702.679 (189.74%) |

## 8. [EishayParseTreeString](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseTreeString.java)
这个场景是将没有格式化的JSON字符串解析为JSONObject或者HashMap，不涉及绑定JavaBean对象。

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	2598.997	|	1542.372 (59.34%)	|	1556.377 (59.88%)	|	1132.437 (43.57%) |
|  | jdk-11.0.20	|	2310.239	|	1133.762 (49.08%)	|	1337.611 (57.9%)	|	1107.294 (47.93%) |
|  | jdk-17.0.8	|	3100.926	|	1543.222 (49.77%)	|	1559.184 (50.28%)	|	1183.083 (38.15%) |
|  | jdk-21.0.2	|	3196.516	|	1454.393 (45.5%)	|	1522.774 (47.64%)	|	1128.01 (35.29%) |
|  | jdk-24	|	3200.912	|	1176.755 (36.76%)	|	1495.48 (46.72%)	|	1294.365 (40.44%) |
|  | graalvm_24+36.1	|	3224.433	|	1921.395 (59.59%)	|	1557.507 (48.3%)	|	1378.458 (42.75%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	2931.279	|	1332.602 (45.46%)	|	1292.835 (44.1%)	|	1313.762 (44.82%) |
|  | jdk-11.0.20	|	3244.684	|	1568.165 (48.33%)	|	1417.204 (43.68%)	|	1200.369 (36.99%) |
|  | zulu17.54.21	|	3443.471	|	1686.731 (48.98%)	|	1552.802 (45.09%)	|	1262.157 (36.65%) |
|  | jdk-21.0.2	|	3449.74	|	1563.898 (45.33%)	|	1328.116 (38.5%)	|	1202.218 (34.85%) |
|  | jdk-24	|	3933.831	|	1621.511 (41.22%)	|	1580.953 (40.19%)	|	1333.869 (33.91%) |
|  | graalvm_24+36.1	|	3860.352	|	2150.078 (55.7%)	|	1782.256 (46.17%)	|	1504.382 (38.97%) |
| MacBookM1Pro | zulu-8.jdk	|	11745.779	|	4784.181 (40.73%)	|	4381.676 (37.3%)	|	3825.42 (32.57%) |
|  | zulu-11.jdk	|	6036.384	|	2848.946 (47.2%)	|	3150.71 (52.2%)	|	3366.472 (55.77%) |
|  | zulu-17.jdk	|	13811.916	|	6214.247 (44.99%)	|	4636.891 (33.57%)	|	4268.707 (30.91%) |
|  | zulu-21.jdk	|	13299.647	|	5466.989 (41.11%)	|	4741.659 (35.65%)	|	4027.568 (30.28%) |
|  | jdk-24.jdk	|	13317.059	|	4640.059 (34.84%)	|	4984.462 (37.43%)	|	4287.21 (32.19%) |
|  | graalvm_24+36.1	|	13167.337	|	7988.911 (60.67%)	|	5007.696 (38.03%)	|	4738.611 (35.99%) |

## 9. [EishayParseTreeStringPretty](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseTreeStringPretty.java)
这个场景是将格式化过的字符串解析为JSONObject或者HashMap，不涉及绑定JavaBean对象。

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	2238.568	|	1346.043 (60.13%)	|	1452.894 (64.9%)	|	1069.735 (47.79%) |
|  | jdk-11.0.20	|	1945.328	|	992.933 (51.04%)	|	1290.615 (66.34%)	|	1057.549 (54.36%) |
|  | jdk-17.0.8	|	2495.659	|	1356.727 (54.36%)	|	1375.46 (55.11%)	|	1078.758 (43.23%) |
|  | jdk-21.0.2	|	2459.192	|	1313.785 (53.42%)	|	1373.076 (55.83%)	|	1071.543 (43.57%) |
|  | jdk-24	|	2608.439	|	1008.918 (38.68%)	|	1465.264 (56.17%)	|	1202.753 (46.11%) |
|  | graalvm_24+36.1	|	2663.39	|	1634.662 (61.38%)	|	1487.68 (55.86%)	|	1272.859 (47.79%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	2465.958	|	1426.484 (57.85%)	|	1295.961 (52.55%)	|	1155.738 (46.87%) |
|  | jdk-11.0.20	|	2755.588	|	1373.707 (49.85%)	|	1396.846 (50.69%)	|	1147.433 (41.64%) |
|  | zulu17.54.21	|	2768.43	|	1471.146 (53.14%)	|	1320.947 (47.71%)	|	1186.949 (42.87%) |
|  | jdk-21.0.2	|	2858.088	|	1340.258 (46.89%)	|	1439.708 (50.37%)	|	1117.302 (39.09%) |
|  | jdk-24	|	3127.782	|	1380.164 (44.13%)	|	1434.811 (45.87%)	|	1235.349 (39.5%) |
|  | graalvm_24+36.1	|	3046.039	|	1837.664 (60.33%)	|	1629.537 (53.5%)	|	1330.094 (43.67%) |
| MacBookM1Pro | zulu-8.jdk	|	10120.143	|	4346.74 (42.95%)	|	4257.517 (42.07%)	|	3982.656 (39.35%) |
|  | zulu-11.jdk	|	5905.897	|	2929.761 (49.61%)	|	2880.939 (48.78%)	|	3255.354 (55.12%) |
|  | zulu-17.jdk	|	10931.736	|	5389.7 (49.3%)	|	4537.861 (41.51%)	|	4049.898 (37.05%) |
|  | zulu-21.jdk	|	10810.953	|	4678.867 (43.28%)	|	4384.745 (40.56%)	|	3943.919 (36.48%) |
|  | jdk-24.jdk	|	10895.494	|	3876.719 (35.58%)	|	4857.909 (44.59%)	|	4061.554 (37.28%) |
|  | graalvm_24+36.1	|	10943.794	|	6806.22 (62.19%)	|	4756.864 (43.47%)	|	4357.059 (39.81%) |

## 10. [EishayParseTreeUTF8Bytes](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseTreeUTF8Bytes.java)
这个场景是将没有格式化的JSON字符串UTF8编码的byte[]数组反序列化解析为JSONObject或者HashMap，不涉及绑定JavaBean对象。

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	2438.755	|	1345.395 (55.17%)	|	1789.999 (73.4%)	|	1033.564 (42.38%) |
|  | jdk-11.0.20	|	2354.753	|	1045.013 (44.38%)	|	1523.285 (64.69%)	|	1100.24 (46.72%) |
|  | jdk-17.0.8	|	3077.76	|	1348.916 (43.83%)	|	1783.563 (57.95%)	|	1114.151 (36.2%) |
|  | jdk-21.0.2	|	3138.498	|	1312.997 (41.84%)	|	1706.734 (54.38%)	|	1074.042 (34.22%) |
|  | jdk-24	|	3183.618	|	1113.694 (34.98%)	|	1704.841 (53.55%)	|	1247.89 (39.2%) |
|  | graalvm_24+36.1	|	3158.332	|	1567.241 (49.62%)	|	1728.968 (54.74%)	|	1331.134 (42.15%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	2828.608	|	1271.374 (44.95%)	|	1398.245 (49.43%)	|	1146.675 (40.54%) |
|  | jdk-11.0.20	|	3272.195	|	1414.163 (43.22%)	|	1719.675 (52.55%)	|	1151.939 (35.2%) |
|  | zulu17.54.21	|	3388.787	|	1492.887 (44.05%)	|	1680.609 (49.59%)	|	1207.738 (35.64%) |
|  | jdk-21.0.2	|	3580.934	|	1397.356 (39.02%)	|	1760.376 (49.16%)	|	1156.109 (32.29%) |
|  | jdk-24	|	3994.985	|	1435.262 (35.93%)	|	1843.903 (46.16%)	|	1277.215 (31.97%) |
|  | graalvm_24+36.1	|	3730.944	|	1740.575 (46.65%)	|	1849.175 (49.56%)	|	1504.46 (40.32%) |
| MacBookM1Pro | zulu-8.jdk	|	10901.561	|	4447.345 (40.8%)	|	5043.7 (46.27%)	|	4371.145 (40.1%) |
|  | zulu-11.jdk	|	6601.083	|	3215.668 (48.71%)	|	3765.665 (57.05%)	|	3385.549 (51.29%) |
|  | zulu-17.jdk	|	13731.271	|	5490.945 (39.99%)	|	5113.088 (37.24%)	|	4249.138 (30.94%) |
|  | zulu-21.jdk	|	13061.945	|	4843.235 (37.08%)	|	4984.488 (38.16%)	|	4072.162 (31.18%) |
|  | jdk-24.jdk	|	13222.398	|	4406.165 (33.32%)	|	5551.153 (41.98%)	|	4367.333 (33.03%) |
|  | graalvm_24+36.1	|	13233.905	|	6005.064 (45.38%)	|	5291.227 (39.98%)	|	4657.876 (35.2%) |

## 11. [EishayParseTreeUTF8BytesPretty](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseTreeUTF8BytesPretty.java)
这个场景是将格式化过的字符串UTF8编码的byte[]数组反序列化解析为JSONObject或者HashMap，不涉及绑定JavaBean对象。

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	1923.805	|	1141.126 (59.32%)	|	1528.066 (79.43%)	|	928.112 (48.24%) |
|  | jdk-11.0.20	|	1999.84	|	883.6 (44.18%)	|	1405.71 (70.29%)	|	1029.057 (51.46%) |
|  | jdk-17.0.8	|	2457.285	|	1150.976 (46.84%)	|	1584.432 (64.48%)	|	1053.334 (42.87%) |
|  | jdk-21.0.2	|	2478.989	|	1188.793 (47.95%)	|	1593.602 (64.28%)	|	1023.37 (41.28%) |
|  | jdk-24	|	2547.988	|	929.482 (36.48%)	|	1594.795 (62.59%)	|	1159.349 (45.5%) |
|  | graalvm_24+36.1	|	2692.059	|	1307.393 (48.56%)	|	1580.523 (58.71%)	|	1205.354 (44.77%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	2400.803	|	1156.555 (48.17%)	|	1479.155 (61.61%)	|	1090.928 (45.44%) |
|  | jdk-11.0.20	|	2730.298	|	1242.721 (45.52%)	|	1582.743 (57.97%)	|	1123.895 (41.16%) |
|  | zulu17.54.21	|	2780.714	|	1333.686 (47.96%)	|	1595.118 (57.36%)	|	1162.038 (41.79%) |
|  | jdk-21.0.2	|	2913.299	|	1245.489 (42.75%)	|	1611.734 (55.32%)	|	1102.266 (37.84%) |
|  | jdk-24	|	3104.977	|	1212.335 (39.04%)	|	1554.699 (50.07%)	|	1202.26 (38.72%) |
|  | graalvm_24+36.1	|	2990.588	|	1445.223 (48.33%)	|	1718.243 (57.46%)	|	1303.747 (43.6%) |
| MacBookM1Pro | zulu-8.jdk	|	9417.279	|	4061.993 (43.13%)	|	4826.762 (51.25%)	|	4169.552 (44.28%) |
|  | zulu-11.jdk	|	5145.855	|	2684.227 (52.16%)	|	3244.562 (63.05%)	|	2853.205 (55.45%) |
|  | zulu-17.jdk	|	10938.677	|	4543.15 (41.53%)	|	4797.959 (43.86%)	|	4202.223 (38.42%) |
|  | zulu-21.jdk	|	10757.314	|	4261.758 (39.62%)	|	4976.7 (46.26%)	|	4120.305 (38.3%) |
|  | jdk-24.jdk	|	10812.854	|	3751.571 (34.7%)	|	5354.164 (49.52%)	|	4168.195 (38.55%) |
|  | graalvm_24+36.1	|	10858.021	|	4950.023 (45.59%)	|	5004.966 (46.09%)	|	4695.354 (43.24%) |

## 12. [EishayParseUTF8Bytes](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseUTF8Bytes.java)
这个场景是将没有格式化的JSON字符串UTF8编码的byte[]数组反序列化为JavaBean对象，是最常用的场景，这个是fastjson1的强项。

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	4123.822	|	2505.163 (60.75%)	|	1649.821 (40.01%)	|	1155.215 (28.01%) |
|  | jdk-11.0.20	|	4249.932	|	2254.233 (53.04%)	|	1493.25 (35.14%)	|	1297.09 (30.52%) |
|  | jdk-17.0.8	|	6088.059	|	2765.071 (45.42%)	|	1596.882 (26.23%)	|	1359.483 (22.33%) |
|  | jdk-21.0.2	|	6159.278	|	2827.199 (45.9%)	|	1523.537 (24.74%)	|	1179.101 (19.14%) |
|  | jdk-24	|	6285.406	|	2445.467 (38.91%)	|	1550.538 (24.67%)	|	1234.949 (19.65%) |
|  | graalvm_24+36.1	|	8020.825	|	3132.978 (39.06%)	|	1392.652 (17.36%)	|	1298.272 (16.19%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	4552.533	|	3168.061 (69.59%)	|	1724.424 (37.88%)	|	1436.651 (31.56%) |
|  | jdk-11.0.20	|	5906.686	|	2854.93 (48.33%)	|	1628.743 (27.57%)	|	1438.848 (24.36%) |
|  | zulu17.54.21	|	6390.229	|	3655.761 (57.21%)	|	1720.89 (26.93%)	|	1562.842 (24.46%) |
|  | jdk-21.0.2	|	6629.545	|	3668.324 (55.33%)	|	1620.416 (24.44%)	|	1360.57 (20.52%) |
|  | jdk-24	|	7190.7	|	3243.051 (45.1%)	|	1730.817 (24.07%)	|	1468.449 (20.42%) |
|  | graalvm_24+36.1	|	7360.936	|	3279.737 (44.56%)	|	1604.14 (21.79%)	|	1484.806 (20.17%) |
| MacBookM1Pro | zulu-8.jdk	|	18138.183	|	11115.01 (61.28%)	|	5596.685 (30.86%)	|	5353.948 (29.52%) |
|  | zulu-11.jdk	|	14102.278	|	6583.556 (46.68%)	|	3705.453 (26.28%)	|	3772.232 (26.75%) |
|  | zulu-17.jdk	|	20721.522	|	13194.297 (63.67%)	|	5226.386 (25.22%)	|	5678.092 (27.4%) |
|  | zulu-21.jdk	|	19487.318	|	13002.16 (66.72%)	|	5215.557 (26.76%)	|	5203.194 (26.7%) |
|  | jdk-24.jdk	|	20602.23	|	11018.537 (53.48%)	|	6000.76 (29.13%)	|	5353.566 (25.99%) |
|  | graalvm_24+36.1	|	28740.966	|	10593.259 (36.86%)	|	5128.109 (17.84%)	|	5158.67 (17.95%) |

## 13. [EishayParseUTF8BytesPretty](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayParseUTF8BytesPretty.java)
这个场景是将格式化过的JSON字符串UTF8编码的byte[]数组反序列化为JavaBean对象

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	3017.001	|	792.298 (26.26%)	|	1511.749 (50.11%)	|	926.977 (30.73%) |
|  | jdk-11.0.20	|	3579.061	|	693.467 (19.38%)	|	1408.919 (39.37%)	|	1040.103 (29.06%) |
|  | jdk-17.0.8	|	4386.145	|	822.23 (18.75%)	|	1488.008 (33.93%)	|	1044.317 (23.81%) |
|  | jdk-21.0.2	|	4199.026	|	796.625 (18.97%)	|	1384.692 (32.98%)	|	1015.498 (24.18%) |
|  | jdk-24	|	4474.838	|	720.062 (16.09%)	|	1389.286 (31.05%)	|	1162.292 (25.97%) |
|  | graalvm_24+36.1	|	4129.404	|	965.364 (23.38%)	|	1305.173 (31.61%)	|	1168.046 (28.29%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	3452.124	|	966.184 (27.99%)	|	1573.39 (45.58%)	|	1079.066 (31.26%) |
|  | jdk-11.0.20	|	3040.291	|	938.112 (30.86%)	|	1566.96 (51.54%)	|	1085.969 (35.72%) |
|  | zulu17.54.21	|	4472.474	|	1026.809 (22.96%)	|	1612.984 (36.06%)	|	1166.46 (26.08%) |
|  | jdk-21.0.2	|	4568.898	|	939.999 (20.57%)	|	1505.562 (32.95%)	|	1079.626 (23.63%) |
|  | jdk-24	|	4871.603	|	897.804 (18.43%)	|	1561.376 (32.05%)	|	1213.632 (24.91%) |
|  | graalvm_24+36.1	|	4846.132	|	1082.778 (22.34%)	|	1435.137 (29.61%)	|	1306.477 (26.96%) |
| MacBookM1Pro | zulu-8.jdk	|	14469.665	|	3315.76 (22.92%)	|	5101.527 (35.26%)	|	4142.057 (28.63%) |
|  | zulu-11.jdk	|	9920.208	|	2013.722 (20.3%)	|	3307.257 (33.34%)	|	3172.562 (31.98%) |
|  | zulu-17.jdk	|	16170.115	|	3165.174 (19.57%)	|	5170.125 (31.97%)	|	4281.512 (26.48%) |
|  | zulu-21.jdk	|	14742.235	|	3241.159 (21.99%)	|	5523.757 (37.47%)	|	4105.915 (27.85%) |
|  | jdk-24.jdk	|	15730.033	|	3118.414 (19.82%)	|	4938.079 (31.39%)	|	4302.376 (27.35%) |
|  | graalvm_24+36.1	|	14297.31	|	3761.356 (26.31%)	|	4638.545 (32.44%)	|	4703.678 (32.9%) |

## 14. [EishayWriteBinary](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteBinary.java)
这个场景是二进制序列化比较，JSONB格式、JSON UTF8编码(fastjson2UTF8Bytes)、hessian、javaSerialize的比较，用于[Apache dubbo](https://github.com/apache/dubbo)的用户选择二进制协议比较

| aliyun ecs spec | jdk version 	|	jsonb	|	msgpack	|	protobuf |
|-----|-----|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	11231.885	|	1540.705 (13.72%)	|	4876.172 (43.41%) |
|  | jdk-11.0.20	|	13513.427	|	1699.283 (12.57%)	|	3866.589 (28.61%) |
|  | jdk-17.0.8	|	16223.589	|	1750.313 (10.79%)	|	5222.619 (32.19%) |
|  | jdk-21.0.2	|	15992.693	|	1685.348 (10.54%)	|	6132.321 (38.34%) |
|  | jdk-24	|	16931.365	|	1674.002 (9.89%)	|	4510.727 (26.64%) |
|  | graalvm_24+36.1	|	13709.366	|	1914.787 (13.97%)	|	5870.936 (42.82%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	9564.996	|	1606.589 (16.8%)	|	5336.194 (55.79%) |
|  | jdk-11.0.20	|	13923.92	|	1916.618 (13.76%)	|	4463.53 (32.06%) |
|  | zulu17.54.21	|	13330.385	|	1947.209 (14.61%)	|	6059.295 (45.45%) |
|  | jdk-21.0.2	|	14708.98	|	1882.203 (12.8%)	|	5717.696 (38.87%) |
|  | jdk-24	|	16361.733	|	2148.885 (13.13%)	|	4603.757 (28.14%) |
|  | graalvm_24+36.1	|	17439.513	|	2112.079 (12.11%)	|	11201.718 (64.23%) |
| MacBookM1Pro | zulu-8.jdk	|	12804.009	|	5405.185 (42.21%)	|	14385.28 (112.35%) |
|  | zulu-11.jdk	|	24825.563	|	4329.219 (17.44%)	|	11047.639 (44.5%) |
|  | zulu-17.jdk	|	24797.602	|	7825.156 (31.56%)	|	18475.809 (74.51%) |
|  | zulu-21.jdk	|	33987.725	|	7301.913 (21.48%)	|	22228.435 (65.4%) |
|  | jdk-24.jdk	|	37422.901	|	7024.375 (18.77%)	|	14694.378 (39.27%) |
|  | graalvm_24+36.1	|	55170.072	|	7515.026 (13.62%)	|	23066.197 (41.81%) |

## 15. [EishayWriteBinaryArrayMapping](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteBinaryArrayMapping.java)
这个场景是二进制序列化比较，JSONB格式（基于字段顺序映射）、kryo、protobuf的比较

| aliyun ecs spec | jdk version 	|	jsonb	|	kryo	|	protobuf |
|-----|-----|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	12917.077	|	5095.691 (39.45%)	|	4600.09 (35.61%) |
|  | jdk-11.0.20	|	15488.817	|	4930.917 (31.84%)	|	5119.352 (33.05%) |
|  | jdk-17.0.8	|	17298.188	|	5635.412 (32.58%)	|	5639.711 (32.6%) |
|  | jdk-21.0.2	|	19383.126	|	5370.35 (27.71%)	|	6148.776 (31.72%) |
|  | jdk-24	|	20397.125	|	4863.221 (23.84%)	|	6189.302 (30.34%) |
|  | graalvm_24+36.1	|	15679.061	|	6161.555 (39.3%)	|	10715.601 (68.34%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	13368.125	|	6429.313 (48.09%)	|	5450.218 (40.77%) |
|  | jdk-11.0.20	|	11699.316	|	5896.076 (50.4%)	|	6105.343 (52.19%) |
|  | zulu17.54.21	|	15935.46	|	6778.808 (42.54%)	|	5313.925 (33.35%) |
|  | jdk-21.0.2	|	15274.578	|	6442.606 (42.18%)	|	5642.909 (36.94%) |
|  | jdk-24	|	22806.764	|	6017.074 (26.38%)	|	5560.775 (24.38%) |
|  | graalvm_24+36.1	|	23172.932	|	6353.604 (27.42%)	|	10572.23 (45.62%) |
| MacBookM1Pro | zulu-8.jdk	|	39884.64	|	9438.14 (23.66%)	|	16312.22 (40.9%) |
|  | zulu-11.jdk	|	45097.807	|	6800.147 (15.08%)	|	10870.73 (24.1%) |
|  | zulu-17.jdk	|	34301.935	|	11945.28 (34.82%)	|	20872.311 (60.85%) |
|  | zulu-21.jdk	|	65428.762	|	11000.577 (16.81%)	|	18655.784 (28.51%) |
|  | jdk-24.jdk	|	60178.658	|	15383.39 (25.56%)	|	20839.886 (34.63%) |
|  | graalvm_24+36.1	|	48061.554	|	11917.422 (24.8%)	|	40197.036 (83.64%) |

## 16. [EishayWriteBinaryAutoType](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteBinaryAutoType.java)
这个场景是带类型信息二进制序列化比较，JSONB格式、JSON UTF8编码(fastjson2UTF8Bytes)、hessian、javaSerialize的比较，用于[Apache dubbo](https://github.com/apache/dubbo)的用户选择二进制协议比较

| aliyun ecs spec | jdk version 	|	fastjson2JSONB	|	hessian	|	javaSerialize |
|-----|-----|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	4479.003	|	1311.249 (29.28%)	|	767.636 (17.14%) |
|  | jdk-11.0.20	|	4791.198	|	1233.93 (25.75%)	|	762.402 (15.91%) |
|  | jdk-17.0.8	|	5990.191	|	1246.141 (20.8%)	|	775.656 (12.95%) |
|  | jdk-21.0.2	|	5779.49	|	1250.43 (21.64%)	|	828.268 (14.33%) |
|  | jdk-24	|	5760.492	|	1338.337 (23.23%)	|	1084.696 (18.83%) |
|  | graalvm_24+36.1	|	5073.213	|	1650.127 (32.53%)	|	978.004 (19.28%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	5308.624	|	1426.265 (26.87%)	|	875.334 (16.49%) |
|  | jdk-11.0.20	|	5937.386	|	1035.705 (17.44%)	|	911.207 (15.35%) |
|  | zulu17.54.21	|	5709.061	|	1273.858 (22.31%)	|	882.796 (15.46%) |
|  | jdk-21.0.2	|	6251.26	|	1237.297 (19.79%)	|	915.687 (14.65%) |
|  | jdk-24	|	6387.335	|	1253.837 (19.63%)	|	1213.623 (19%) |
|  | graalvm_24+36.1	|	6070.421	|	1282.804 (21.13%)	|	1134.718 (18.69%) |
| MacBookM1Pro | zulu-8.jdk	|	15278.026	|	2425.357 (15.87%)	|	3368.58 (22.05%) |
|  | zulu-11.jdk	|	11903.158	|	2206.69 (18.54%)	|	1986.432 (16.69%) |
|  | zulu-17.jdk	|	17804.609	|	2024.137 (11.37%)	|	3216.851 (18.07%) |
|  | zulu-21.jdk	|	20511.867	|	2256.369 (11%)	|	3868.031 (18.86%) |
|  | jdk-24.jdk	|	16570.611	|	2791.58 (16.85%)	|	5260.845 (31.75%) |
|  | graalvm_24+36.1	|	18106.176	|	2760.039 (15.24%)	|	5076.142 (28.04%) |

## 17. [EishayWriteString](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteString.java)
这个场景是将JavaBean对象序列化为字符串

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	6050.448	|	1891.812 (31.27%)	|	2655.472 (43.89%)	|	1238.394 (20.47%) |
|  | jdk-11.0.20	|	6454.351	|	1829.941 (28.35%)	|	2411.345 (37.36%)	|	922.956 (14.3%) |
|  | jdk-17.0.8	|	6881.313	|	1913.168 (27.8%)	|	2724.584 (39.59%)	|	1163.11 (16.9%) |
|  | jdk-21.0.2	|	6796.254	|	1848.992 (27.21%)	|	2517.909 (37.05%)	|	1107.802 (16.3%) |
|  | jdk-24	|	6818.959	|	2102.882 (30.84%)	|	2483.626 (36.42%)	|	1045.473 (15.33%) |
|  | graalvm_24+36.1	|	8666.779	|	2360.073 (27.23%)	|	2556.632 (29.5%)	|	1006.626 (11.61%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	5646.65	|	2313.878 (40.98%)	|	2616.449 (46.34%)	|	1677.162 (29.7%) |
|  | jdk-11.0.20	|	6959.624	|	2286.255 (32.85%)	|	2810.918 (40.39%)	|	1290.811 (18.55%) |
|  | zulu17.54.21	|	6917.69	|	2246.867 (32.48%)	|	2977.437 (43.04%)	|	938.04 (13.56%) |
|  | jdk-21.0.2	|	6647.406	|	2031.976 (30.57%)	|	2734.415 (41.14%)	|	921.209 (13.86%) |
|  | jdk-24	|	7216.581	|	3009.308 (41.7%)	|	2968.727 (41.14%)	|	959.983 (13.3%) |
|  | graalvm_24+36.1	|	8275.642	|	2959.177 (35.76%)	|	2954.223 (35.7%)	|	868.245 (10.49%) |
| MacBookM1Pro | zulu-8.jdk	|	16237.652	|	8637.777 (53.2%)	|	12006.562 (73.94%)	|	5712.372 (35.18%) |
|  | zulu-11.jdk	|	14648.394	|	4925.396 (33.62%)	|	5931.863 (40.49%)	|	2620.437 (17.89%) |
|  | zulu-17.jdk	|	20298.947	|	7718.1 (38.02%)	|	9341.16 (46.02%)	|	4364.411 (21.5%) |
|  | zulu-21.jdk	|	17152.283	|	6999.309 (40.81%)	|	9026.126 (52.62%)	|	4260.293 (24.84%) |
|  | jdk-24.jdk	|	22802.499	|	8736.275 (38.31%)	|	10330.361 (45.3%)	|	4284.116 (18.79%) |
|  | graalvm_24+36.1	|	23583.227	|	8701.55 (36.9%)	|	8750.264 (37.1%)	|	3358.606 (14.24%) |

## 18. [EishayWriteStringTree](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteStringTree.java)
这个场景是将JSONObject或者Map序列化为字符串

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	4125.53	|	2405.961 (58.32%)	|	2419.388 (58.64%)	|	1438.893 (34.88%) |
|  | jdk-11.0.20	|	4017.563	|	2316.927 (57.67%)	|	2442.495 (60.8%)	|	983.284 (24.47%) |
|  | jdk-17.0.8	|	3914.014	|	2234.115 (57.08%)	|	2542.214 (64.95%)	|	1265.567 (32.33%) |
|  | jdk-21.0.2	|	4178.011	|	2273.479 (54.42%)	|	2491.842 (59.64%)	|	1233.889 (29.53%) |
|  | jdk-24	|	4194.648	|	2325.229 (55.43%)	|	2546.149 (60.7%)	|	1162.411 (27.71%) |
|  | graalvm_24+36.1	|	4973.903	|	2568.34 (51.64%)	|	2597.773 (52.23%)	|	1082.17 (21.76%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	3617.569	|	2474.966 (68.42%)	|	2751.065 (76.05%)	|	1809.383 (50.02%) |
|  | jdk-11.0.20	|	4141.828	|	2647.189 (63.91%)	|	2540.282 (61.33%)	|	1393.93 (33.65%) |
|  | zulu17.54.21	|	4470.902	|	2760.681 (61.75%)	|	2733.211 (61.13%)	|	957.938 (21.43%) |
|  | jdk-21.0.2	|	5500.756	|	2641.262 (48.02%)	|	2723.665 (49.51%)	|	993.916 (18.07%) |
|  | jdk-24	|	5875.521	|	2717.974 (46.26%)	|	2745.728 (46.73%)	|	1003.389 (17.08%) |
|  | graalvm_24+36.1	|	5287.333	|	2967.489 (56.12%)	|	3123.561 (59.08%)	|	932.335 (17.63%) |
| MacBookM1Pro | zulu-8.jdk	|	11547.15	|	8766.271 (75.92%)	|	10774.951 (93.31%)	|	6022.31 (52.15%) |
|  | zulu-11.jdk	|	9540.85	|	5822.979 (61.03%)	|	5952.448 (62.39%)	|	2779.499 (29.13%) |
|  | zulu-17.jdk	|	12441.625	|	8025.532 (64.51%)	|	8236.33 (66.2%)	|	4300.977 (34.57%) |
|  | zulu-21.jdk	|	14716.227	|	7707.237 (52.37%)	|	8483.983 (57.65%)	|	4398.435 (29.89%) |
|  | jdk-24.jdk	|	12989.656	|	8809.001 (67.82%)	|	9737.072 (74.96%)	|	4491.406 (34.58%) |
|  | graalvm_24+36.1	|	13426.154	|	10196.895 (75.95%)	|	10220.265 (76.12%)	|	3432.077 (25.56%) |

## 19. [EishayWriteUTF8Bytes](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteUTF8Bytes.java)
这个场景是将JavaBean对象序列化为UTF8编码的Bytes

| aliyun ecs spec | jdk version 	|	fastjson2	|	fastjson1	|	jackson	|	gson |
|-----|-----|----------|----------|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	5941.741	|	2287.944 (38.51%)	|	2457.187 (41.35%)	|	1140.075 (19.19%) |
|  | jdk-11.0.20	|	7394.891	|	1637.408 (22.14%)	|	2242.211 (30.32%)	|	882.6 (11.94%) |
|  | jdk-17.0.8	|	8520.012	|	3068.233 (36.01%)	|	2520.572 (29.58%)	|	1144.162 (13.43%) |
|  | jdk-21.0.2	|	8395.558	|	1632.709 (19.45%)	|	2595.824 (30.92%)	|	1089.212 (12.97%) |
|  | jdk-24	|	8522.696	|	1857.972 (21.8%)	|	2368.066 (27.79%)	|	1021.923 (11.99%) |
|  | graalvm_24+36.1	|	9435.882	|	1964.788 (20.82%)	|	2767.586 (29.33%)	|	980.686 (10.39%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	6244.712	|	2066.606 (33.09%)	|	2969.68 (47.56%)	|	1350.396 (21.62%) |
|  | jdk-11.0.20	|	6797.782	|	1996.866 (29.38%)	|	2713.586 (39.92%)	|	1294.449 (19.04%) |
|  | zulu17.54.21	|	7460.168	|	2064.44 (27.67%)	|	2980.481 (39.95%)	|	927.564 (12.43%) |
|  | jdk-21.0.2	|	7949.134	|	1654.992 (20.82%)	|	2696.819 (33.93%)	|	891.149 (11.21%) |
|  | jdk-24	|	8279.567	|	2145.437 (25.91%)	|	2633.496 (31.81%)	|	942.785 (11.39%) |
|  | graalvm_24+36.1	|	9200.608	|	2258.268 (24.54%)	|	3246.497 (35.29%)	|	864.579 (9.4%) |
| MacBookM1Pro | zulu-8.jdk	|	18840.858	|	7305.889 (38.78%)	|	10582.082 (56.17%)	|	4969.545 (26.38%) |
|  | zulu-11.jdk	|	18007.729	|	4856.901 (26.97%)	|	6176.293 (34.3%)	|	2262.158 (12.56%) |
|  | zulu-17.jdk	|	21632.768	|	7781.974 (35.97%)	|	9721.074 (44.94%)	|	4225.104 (19.53%) |
|  | zulu-21.jdk	|	23922.264	|	6894.902 (28.82%)	|	8975.819 (37.52%)	|	4247.56 (17.76%) |
|  | jdk-24.jdk	|	25842.006	|	7262.758 (28.1%)	|	10247.56 (39.65%)	|	4211.943 (16.3%) |
|  | graalvm_24+36.1	|	34947.012	|	7630.652 (21.83%)	|	10343.169 (29.6%)	|	3330.388 (9.53%) |

## 20. [EishayWriteUTF8BytesTree](https://github.com/alibaba/fastjson2/blob/main/benchmark/src/main/java/com/alibaba/fastjson2/benchmark/eishay/EishayWriteUTF8BytesTree.java)
这个场景是将JSONObject或者Map序列化为UTF8编码的Bytes

| aliyun ecs spec | jdk version 	|	fastjson2	|	jackson |
|-----|-----|----------|-----|
| aliyun_ecs.c8a.large | jdk1.8.0_381	|	4344.944	|	2535.586 (58.36%) |
|  | jdk-11.0.20	|	3983.036	|	1996.587 (50.13%) |
|  | jdk-17.0.8	|	4474.692	|	2261.139 (50.53%) |
|  | jdk-21.0.2	|	4614.91	|	2521.926 (54.65%) |
|  | jdk-24	|	4771.445	|	2191.168 (45.92%) |
|  | graalvm_24+36.1	|	4299.101	|	2557.922 (59.5%) |
| [aliyun_ecs.g8y.large](https://www.alibabacloud.com/zh/product/ecs/g8y) | zulu8.82.0.21	|	5032.435	|	3425.187 (68.06%) |
|  | jdk-11.0.20	|	4564.741	|	2355.832 (51.61%) |
|  | zulu17.54.21	|	5115.439	|	2927.199 (57.22%) |
|  | jdk-21.0.2	|	5260.225	|	2946.509 (56.01%) |
|  | jdk-24	|	6328.531	|	2194.382 (34.67%) |
|  | graalvm_24+36.1	|	5058.438	|	3388.244 (66.98%) |
| MacBookM1Pro | zulu-8.jdk	|	11114.544	|	9798.32 (88.16%) |
|  | zulu-11.jdk	|	8509.322	|	5771.817 (67.83%) |
|  | zulu-17.jdk	|	13311.165	|	9639.503 (72.42%) |
|  | zulu-21.jdk	|	13447.234	|	9847.215 (73.23%) |
|  | jdk-24.jdk	|	16138.442	|	7783.283 (48.23%) |
|  | graalvm_24+36.1	|	14442.772	|	9834.735 (68.09%) |

