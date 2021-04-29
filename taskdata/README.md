This corpora is obtained from comment texts of Weibo. Three categories of texts are considered in this task, which are COVID-19, Trade War and Tokyo Olympic Games. All data are split into 2 datasets for training and testing. 

#### Category description

##### Subject:

COVID-19's prevention and control

##### Defination:

COVID-19's prevention and control means various preventive control measures taken by governments, hospitals and other organizations during the period of COVID-19 against its spread, including policies and regulations about masks, vaccines and home quarantine.

“疫情防控”主要指新冠疫情期间，各国政府，医院，民众及其它组织针对疫情蔓延所作出的各类预防管控措施，包括政策、管理条例、口罩、疫苗、隔离等。

对应负样本主要是新冠的影响、溯源、扩散状况等子事件。同时，为凸显子事件边界，数据还引入了少量其它新冠相关样本和新冠无关的负样本。 

##### Example:

> CDC还有一条提示，感觉也有意义：摘下口罩再戴时，手的洁净至关重要。建议洗手后再戴口罩。
>
> Label：1

> 到底病毒来自哪里还没有答案。最可怕的是，如果另外病毒肆虐，人类怎么办？
>
> Label：0 

##### Subject:

Trade actions of US towards China during trade war

##### Defination:

The actions of US to reduce the trade deficit with China, including imposing tariffs of Chinese imports and restricting the ability of Chinese companies to trade with US firms.

“美国贸易战举措”主要指在中美贸易战期间，美国处于某些政治目的，出台一系列压制我国经济贸易发展的举措，包括打压我国民营企业，加征关税等。

负样本主要是中美贸易战期间的中方举措，美方制裁和中方反制裁这两类事件具有相同的语境，不同点主要体现在主客体的差异（美方发起贸易争端是美国为主体，中国为客体，中方反制裁是中方为主体，美方为客体），故对于事件识别是一个巨大的挑战。 

##### Example:

> 美国商务部18日以“违反美国国家安全” 为由，宣布将包括大疆公司在内的包括59家中国实体列入所谓出口管制“实体清单”。据路透社20日报道，大疆在给该媒体一份邮件声明中，对被美国政府列入清单做出回应。
>
> Label：1

> 商务部副部长兼国际贸易谈判副代表王受文表示：中方不愿打，但不怕打“贸易战”。如果有人坚持打，我们奉陪到底。谈判、磋商解决问题的大门是敞开的，如果美方愿意谈，我们愿在平等磋商、相互尊重的基础上磋商，解决分歧。
>
> Label：0 

##### Subject:

The Tokyo Olympic Games will be postponed or held as scheduled

##### Defination:

The Tokyo Olympic Games would not be cancelled, it will be held as scheduled or postponed.

“东京奥运会举办”主要指国际上为了避免东京奥运会的取消所发布的相关举措与国际发声等。

所对应负样本主要是各种因素作用下可能导致东京奥运会停办，民众对此事件的各种声音。其区别在于判别最终奥运会是否能够举行。同时，为凸显子事件边界，数据还引入了少量其它奥运会相关样本和奥运会无关的负样本。 

##### Example:

> 为了维护运动员的健康，参加奥运会的每个人和国际社会，原定在东京举行的夏季奥运会及残奥运会重新安排到2020年以后，但不得晚于2021年夏天。 
>
> Label：1

> 这个有什么好讨论的，疫情太严重当然取消啊，不然呢？换你你敢冒着生命危险去参赛？什么运动员准备了四年不四年的，就不用你操心了，相比四年一次的奥运会，运动员更希望自己健康长寿好吗？况且比奥运会含金量更大的是世锦赛。
>
> Label：0 

#### Train dataset

1. Unlabelled corpus containing 100K samples related to the sub-events.
2. Samples with specific categories, 100 labeled samples per sub-event.

#### Test dataset

Samples with specific categories, 2000 labeled samples per sub-event.