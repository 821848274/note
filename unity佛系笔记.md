### 项目基础设置



![image-20251029214820315](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251029214820315-1761745702764-1-1761745707373-3.png)





窗口设置为2 X 3

![image-20251029215639456](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251029215639456-1761746201616-5.png)

设置unity的默认编辑代码工具





![image-20251029215905799](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251029215905799-1761746346970-7.png)

vscode中安装插件





### 常用数据类型



int

boolean

float

string

## 开发步骤

![image-20251029221933663](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251029221933663-1761747574830-9.png)



### 碰撞问题

可以在组件添加里面找到colider



![image-20251109091916219](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251109091916219-1762651160789-1.png)



### 物体材质问题



创建材质,设置好颜色拖到物体上面



### 物体映射移动问题

![image-20251103005750607](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251103005750607-1762102672004-3.png)



![image-20251103005825068](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251103005825068-1762102706621-5.png)

### 摄像机角度问题

选中射线机,调整到自己观看舒服的角度 ctrl+shift+f



### 摄像机角度问题2

给摄像机添加一个脚本

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class sheXiangJi : MonoBehaviour
{

    public GameObject playerController;
    Vector3 offset;
    // Start is called before the first frame update
    void Start()
    {
        offset = transform.position - playerController.transform.position;
    }

    // Update is called once per frame
    void Update()
    {
        transform.position = playerController.transform.position + offset;
    }
}

```



暴露出来的playerController 属性,需要在unity界面拖动小球赋值,这样playerController就能获取到值了



### 左上角的text文本计数问题

![image-20251104231143059](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251104231143059-1762269106536-1.png)



左键点击Canvas  聚焦游戏窗口,摁 F 切换视角  

然后点击texttmp 调整窗口定位,调整text定位,

在主角上暴露出public TMP_Text countText_TMP; text的属性

unity中拖动text组件赋值,然后设置小球吃的数量

#### 不显示中文问题

https://www.bilibili.com/video/BV1nm4y117T8/?spm_id_from=333.337.search-card.all.click&vd_source=4e22ef4c70dd59786dcb8a48c0368192



https://blog.csdn.net/qq_44773469/article/details/154064020







# 小技巧(上)

## 1.运行模式下的编辑器着色问题

![image-20251106225451242](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251106225451242-1762440895346-1.png)



![image-20251106225541534](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251106225541534-1762440942417-3.png)



只要在运行时更改游戏内容,编辑器会变色

## 2.运行时改动的保留方法

在运行时改动,复制组件,关闭游戏,重新找到组件把刚才复制的组件属性粘贴上去,保存



![image-20251106230026839](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251106230026839-1762441227800-5.png)





## 3.单位快速对齐

![image-20251107215437073](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251107215437073-1762523680439-1.png)



如果找不到 overlay menu 里调用出来 可以调整每次对齐的单位量



![image-20251107215618741](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251107215618741-1762523780172-3.png)

ctrl + 鼠标左键可以定向移动或者转换角度



## 4.定点快速对齐

如果有两个物体重叠,想要快速定点对齐,可以选中一个摁住V 键,鼠标左键选择两个物体对齐的顶点,然后移动物体



## 5.表面快速对齐

将两个物体表面贴合,要注意物体要有碰撞体

ctrl + shift + 鼠标左键(移动物体/选中物体状态下)

![image-20251107221049153](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251107221049153-1762524650513-5.png)

这里调成pivot 可以变成轴心对齐

## 6.网格快速对齐

![image-20251108211115789](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108211115789-1762607480021-1.png)



在global状态下,

把图表点亮,就可以网格对齐移动了

## 7.网格显示和调整



![image-20251108211350321](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108211350321-1762607631302-3.png)



## 8.释放资源预览窗口

点击图片时,可以点击图片右上角的三个点,进行放大观看,不想看了关闭就行

![image-20251108211853443](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108211853443-1762607934941-5.png)

## 9.场景视图中显示图标

![image-20251108212116923](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108212116923-1762608078038-7.png)



## 10.场景视图中隐藏对象

![image-20251108212225018](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108212225018-1762608146102-9-1762609203745-11.png)



## 11.场景视图中禁选对象



![image-20251108214142084](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108214142084-1762609303165-13.png)



## 12.场景视图中聚焦对象



双击对象可以聚焦/摁F键可以聚焦

如果是移动对象:



![image-20251108214415206](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108214415206-1762609456272-15.png)





# 小技巧(下)

## 1.通过组件查找对象



可以通过没有空格的全称来查找/复制组件的脚本文件名称,粘贴到搜索框实现查找



![image-20251108214742871](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108214742871-1762609664055-17.png)

## 2.通过标签搜索资源

资源右下角有个可以添加资源的图标



![image-20251108221046118](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108221046118-1762611048137-29.png)



![image-20251108215138330](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108215138330-1762609899556-19.png)



## 3.快速搜索

![image-20251108215247280](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108215247280-1762609968717-21.png)

去 package manager下载 quick search

## 4.文档搜索捷径

可以点击属性旁边的问号/去package manager 下载相应的资源包,再下载资源包的文档

## 5.新建脚本捷径

添加组件后直接输入脚本名称,连恩两次回车

![image-20251108215930470](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108215930470-1762610371547-23.png)

## 6.展收层级捷径

alt+左键

## 7.摄像机摆位捷径

选中射线机,调整到自己观看舒服的角度 ctrl+shift+f



![image-20251108220304026](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108220304026-1762610585542-25.png)



## 8.快捷键管理器

shortcut 可以修改快捷键



![image-20251108220551139](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251108220551139-1762610752470-27.png)





# 3D坦克



```c#
rg.velocity.normalized
    
normalized 是向量的归一化,斜着走的话最大值也是1而不是根号2
```





#### 移动物体的普遍方式

```c#
var qianHou = Input.GetAxis("Vertical");
var zuoYou = Input.GetAxis("Horizontal");

// transform.position += new Vector3(zuoYou, 0, qianHou)* moveSpeed * Time.deltaTime;

transform.Translate(new Vector3(zuoYou, 0, qianHou) * moveSpeed * Time.deltaTime);
```





### 角色会摔倒问题:锁轴



![image-20251119223214708](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251119223214708-1763562739355-1.png)





```c#
        var qianHou = Input.GetAxis("Vertical");
        var zuoYou = Input.GetAxis("Horizontal");

        // transform.position += new Vector3(zuoYou, 0, qianHou)* moveSpeed * Time.deltaTime;

        // transform.Translate(new Vector3(zuoYou, 0, qianHou) * moveSpeed * Time.deltaTime);

        // rigidbody.velocity = new Vector3(0, 0, 1) * qianHou * moveSpeed;
        // rigidbody.angularVelocity = new Vector3(0, 1, 0) * zuoYou * jiaoDuSpeed;
        
        rigidbody.velocity = transform.forward * qianHou * moveSpeed;
        
        rigidbody.angularVelocity = transform.up * zuoYou * jiaoDuSpeed;
```





### 多物体共同移动问题:父子级关系



把子集直接鼠标拖动到父级下面

一般都是空白地方右键创建空对象,作为父级



空对象-->cube

添加两个组件

1.mesh filter 里面选择cube形状

2.mesh renderer  里面选择材质

![image-20251119232130579](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251119232130579-1763565691613-3.png)

### 空对象:空气墙

添加组件  box collider,编辑碰撞器

![image-20251119232557695](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251119232557695-1763565960120-5.png)

### prefeb预制体:模板



直接拖动想要变成模版的组件-->文件编辑区域,然后编辑成想要的模样,点击左上角返回



使用:直接拖动文件区域的模板到动画区域

### 新建场景:地图切换



file->new scene -> basic



切换回来:

Scenes文件夹里面 双击想要回到的场景



# 下载美术资源



asset store  里面下载美术资源



package manager 资源包管理器



![image-20251120204546445](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251120204546445-1763642751117-1.png)



### 地面的设置

拖动leveArt到页面中央,

window-->rendering-->lighting   

点击Environment页面

Environment Lighting

​		Source-->Color



接着设置Ambient Color-->72,62,113



### 坦克的设置

拖动models里面的tank到组件里面

添加Box Collider,然后编辑

![image-20251120212452615](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251120212452615-1763645094823-3.png)



### 摄像机的设置



设置摄像机的位置和角度

设置背景类型为纯色

颜色80,60,50



修改投影方式为正交

区别:

​	透视:不遵从近大远小(默认)

​	正交:遵从近大远小

![image-20251120212941490](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251120212941490-1763645383205-5.png)

![image-20251120213221729](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251120213221729-1763645543011-7.png)

![image-20251120213536845](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251120213536845-1763645738276-9.png)



### 坦克的移动



```c#
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TankMove : MonoBehaviour
{

    public int moveSpeed = 20;
    public int trunSpeed = 180;




    private string qianHouStr;
    private string xuanZhuanStr;
    private float qianHou;
    private float xuanZhuan;
    private float trunVal;

    Rigidbody rigidbody;
    // Start is called before the first frame update
    void Start()
    {
        qianHouStr = "Vertical";
        xuanZhuanStr = "Horizontal";

        rigidbody = transform.GetComponent<Rigidbody>();
    }

    // Update is called once per frame
    void Update()
    {
        qianHou = Input.GetAxis(qianHouStr);
        xuanZhuan = Input.GetAxis(xuanZhuanStr);

        // transform.position();

        rigidbody.MovePosition(transform.forward * qianHou * moveSpeed * Time.deltaTime + rigidbody.position);


        trunVal = xuanZhuan * trunSpeed * Time.deltaTime;
        Quaternion quaternion = Quaternion.Euler(0, trunVal, 0);
        rigidbody.MoveRotation(quaternion * rigidbody.rotation);
    }
}

```



##### 还要锁住重力组件里面的X,Z角度

修改过后的代码

#### FixedUpdate():固定帧率



```c#
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.PlayerLoop;

public class TankMove : MonoBehaviour
{

    public int moveSpeed = 20;
    public int trunSpeed = 180;




    private string qianHouStr;
    private string xuanZhuanStr;
    private float qianHou;
    private float xuanZhuan;
    private float trunVal;

    Rigidbody rigidbody;
    // Start is called before the first frame update
    void Start()
    {
        qianHouStr = "Vertical";
        xuanZhuanStr = "Horizontal";

        rigidbody = transform.GetComponent<Rigidbody>();
    }

    // Update is called once per frame
    void Update()
    {
        qianHou = Input.GetAxis(qianHouStr);
        xuanZhuan = Input.GetAxis(xuanZhuanStr);

        // transform.position();
    }


    private void FixedUpdate()
    {
        move();
        turn();
    }

    private void turn()
    {
        trunVal = xuanZhuan * trunSpeed * Time.deltaTime;
        Quaternion quaternion = Quaternion.Euler(0, trunVal, 0);
        rigidbody.MoveRotation(quaternion * rigidbody.rotation);
    }


    private void move()
    {
        rigidbody.MovePosition(transform.forward * qianHou * moveSpeed * Time.deltaTime + rigidbody.position);
    }

}

```



### 音效问题

添加音效组件 audio source -->选择默认的音效,拖动到组件中,LOOP循环播放选择打开



将新建组件拖动到public AudioSource movementAudio;赋值



新建几个需要切换的声音,暴露出来赋值



```c#
public AudioSource movementAudio; 
public AudioClip engineIdling;       
public AudioClip engineDriving;   


void Update()
    {
        qianHou = Input.GetAxis(qianHouStr);
        xuanZhuan = Input.GetAxis(xuanZhuanStr);

        // transform.position();
        // Debug.Log(Math.Abs(qianHou));

        if(Math.Abs(qianHou) < 0.1 && Math.Abs(xuanZhuan) < 0.1)
        {
            if(movementAudio.clip == engineDriving)
            {
                movementAudio.clip = engineIdling;
                movementAudio.Play();
            }

        }
        else
        {
            if(movementAudio.clip == engineIdling)
            {
                movementAudio.clip = engineDriving;
                movementAudio.Play();
            }
        }
    }
```





### 增加音高问题

可以不使用0.8-1.2随机数,

比较旋转和前进的大数,然后根据比例来改变声音的音高

eg: 不动时 0.5,最大值1.5,差值1

获取大数的值0.8是1的80%,音高就是0.5+0.8=1.3



```c#

originalPitch = movementAudio.pitch;

void Start()
    {
        qianHouStr = "Vertical";
        xuanZhuanStr = "Horizontal";

        rigidbody = transform.GetComponent<Rigidbody>();

        originalPitch = movementAudio.pitch;
    }

    // Update is called once per frame
    void Update()
    {
        qianHou = Input.GetAxis(qianHouStr);
        xuanZhuan = Input.GetAxis(xuanZhuanStr);

        // transform.position();
        // Debug.Log(Math.Abs(qianHou));

        if(Mathf.Abs(qianHou) < 0.1 && Mathf.Abs(xuanZhuan) < 0.1)
        {
            if(movementAudio.clip == engineDriving)
            {
                movementAudio.clip = engineIdling;
                // movementAudio.pitch = 0.5f;
                movementAudio.pitch = Random.Range(originalPitch - pitchRange,originalPitch + pitchRange);
                movementAudio.Play();
            }

        }
        else
        {
            if(movementAudio.clip == engineIdling)
            {
                movementAudio.clip = engineDriving;
                // movementAudio.pitch = 0.5f + (Math.Abs(qianHou) + Math.Abs(xuanZhuan))/2;
                movementAudio.pitch = Random.Range(originalPitch - pitchRange,originalPitch + pitchRange);
                movementAudio.Play();
            }
        }
    }

```





### 坦克尾巴烟尘效果

prefabs-->DustTrail文件拖动到角色下面

![image-20251123174557559](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251123174557559-1763891161189-1.png)





### 炮弹发射问题

#### 创建炮弹组件

炮弹发射的起始位置

tank下面创建一个空对象,设置位置

tips:如果角度没有变化,别忘了global换成lacal



![image-20251123195501341](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251123195501341-1763898902700-3.png)



![image-20251123195635099](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251123195635099-1763898996321-5.png)



#### 炮弹生成问题



暴露炮弹组件和模型组件,把上面创建的炮弹组件赋值给暴露出来的属性,models-->shell 赋值给模型组件





```c#
public GameObject paoDanObject;
public GameObject paoDanModelObject;
fire1Str = "Fire1";
   void Update()
    {
        if (Input.GetButton(fire1Str))
        {
            GameObject paoDanInstance = Instantiate(paoDanModelObject, paoDanObject.transform.position, paoDanObject.transform.rotation);
        }

    }

```



##### 问题:炮弹只生成悬浮空中不动

原因:没给炮弹相应的组件

解决办法:把shell拖到组件里面,然后再拖到prefabs里面做成模版,添加重力,碰撞体等组件,替换掉tank对象的paodanModel



### 炮弹的蓄力完善

将原来的炮弹代码移到自己的脚本中,





```c#
void Start()
    {
        FireStr = "Fire";
        m_FireButton = FireStr + m_PlayerNumber;

        m_ChargeSpeed = (m_MaxLaunchForce - m_MinLaunchForce) / m_MaxChargeTime;

    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetButtonDown(m_FireButton))
        {
            m_CurrentLaunchForce = m_MinLaunchForce;
        }
        else if (Input.GetButton(m_FireButton))
        {
            m_CurrentLaunchForce += m_ChargeSpeed * Time.deltaTime;
            m_CurrentLaunchForce = m_CurrentLaunchForce >= m_MaxLaunchForce ? m_MaxLaunchForce : m_CurrentLaunchForce;

            if (m_CurrentLaunchForce >= m_MaxLaunchForce)
            {
                Fire();
            }
        }
        else if (Input.GetButtonUp(m_FireButton))
        {
            Fire();
        }
    }

    void Fire()
    {
        GameObject paoDanInstance = Instantiate(paoDanModelObject, paoDanObject.transform.position, paoDanObject.transform.rotation);

        Rigidbody paoDanInstanceRigidbody = paoDanInstance.GetComponent<Rigidbody>();

        paoDanInstanceRigidbody.velocity = paoDanObject.transform.forward * m_CurrentLaunchForce;

        m_CurrentLaunchForce = m_MinLaunchForce;
    }

```





### 炮弹声音问题

添加audio source 组件,关闭 play on awake ,不添加原音



给暴露的炮弹声音属性赋值,炮弹脚本中添加声音

![image-20251123224546674](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251123224546674-1763909148350-7.png)



![image-20251123230228442](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251123230228442-1763910149362-11.png)



```c#
void Update()
    {
        if (Input.GetButtonDown(m_FireButton))
        {
            m_CurrentLaunchForce = m_MinLaunchForce;
        }
        else if (Input.GetButton(m_FireButton))
        {
            m_CurrentLaunchForce += m_ChargeSpeed * Time.deltaTime;

            if (m_ShootingAudio.clip == m_FireClip)
            {
                m_ShootingAudio.clip = m_ChargingClip;
                m_ShootingAudio.Play();
            }


            m_CurrentLaunchForce = m_CurrentLaunchForce >= m_MaxLaunchForce ? m_MaxLaunchForce : m_CurrentLaunchForce;

            if (m_CurrentLaunchForce >= m_MaxLaunchForce)
            {
                Fire();
            }
        }
        else if (Input.GetButtonUp(m_FireButton))
        {
            Fire();
        }
    }




void Fire()
    {
        GameObject paoDanInstance = Instantiate(paoDanModelObject, paoDanObject.transform.position, paoDanObject.transform.rotation);

        Rigidbody paoDanInstanceRigidbody = paoDanInstance.GetComponent<Rigidbody>();

        paoDanInstanceRigidbody.velocity = paoDanObject.transform.forward * m_CurrentLaunchForce;

        m_CurrentLaunchForce = m_MinLaunchForce;

        m_ShootingAudio.clip = m_FireClip;
        m_ShootingAudio.Play();
    }
```



#### 问题:当蓄力完再松开时会额外发射一发炮弹

原因:按键蓄力时进入方法,会发射炮弹,松开按键时会进入松开方法再发射一发炮弹

解决方法:用boolean判断是否发射



```c#
else if (Input.GetButton(m_FireButton) && m_Fired == false)
else if (Input.GetButtonUp(m_FireButton) && m_Fired == false)
```





### 多角色移动问题





```c#
// 坦克移动里面添加
qianHouStr = "Vertical" + m_PlayerNumber;
xuanZhuanStr = "Horizontal" + m_PlayerNumber;

// 坦克炮弹里面添加
m_FireButton = FireStr + m_PlayerNumber;
```







### 炮弹销毁/触发器问题



拖动shell预制体,添加炮弹销毁脚本-->覆盖到预制体





![image-20251124234703581](./unity%E4%BD%9B%E7%B3%BB%E7%AC%94%E8%AE%B0.assets/image-20251124234703581-1763999227583-1.png)



```c#
	// 炮弹销毁
		void Start()
    {
        Destroy(gameObject, m_MaxLifeTime);
    }
```





# 36
