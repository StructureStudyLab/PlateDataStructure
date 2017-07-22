#配筋设计说明

## 需求


[Shared Type Parameter--给墙添加实例参数](http://thebuildingcoder.typepad.com/blog/2010/07/shared-type-parameter.html)
## 开发思路



##开发


~~~mermaid
graph LR
    Funcions-->Add/DeleteRebar;Add/DeleteRebar-->|DMU|PutInCRebarES;
    Funcions-->Add/DeleteRebarTag;Add/DeleteRebarTag-->|DMU|PutInCRebarTag;
    Funcions-->|Wall/Plate Change|UpdateRebarTags;
    Funcions-->|RebarTags Change|UpdateRebarLeaderLines;
    Funcions-->SetAreaRebarTags;SetAreaRebarTags-->CAreaRebarES::setAroundRebarIds;
    Funcions-->RebarSharedParameters;RebarSharedParameters-->|DMU|RebarProperty;
~~~
![Alt text](https://g.gravizo.com/svg?
/**
*@opt all
*@note constVar
*/
class constVar {
    static public double m_textHeight;
    static public double m_textHeight1;
    static public double m_textHeight2;
    static public double m_rebarNoteAgainstLeader;
    static public double m_rebarLeaderAgainstHost;
}
/**
*@opt all
*@note Wall Sysytem Parameters
*/
class SystemWallFamily {
    static public string m_wallName;
    static public string m_wallFunction;
}
)

![Alt text](https://g.gravizo.com/svg?
/**
*@opt all
*@note RebarTag
*/
class CRebarTag {
    static public ElementID m_tagId;
    static public ElementID m_rebarId;
    static public bool m_isMiddle;
    static public bool m_isVerticle;
    static public double m_offset;
    static public ElementID m_leftElement;
    static public ElementID m_rightElement;
    static public ElementIDs m_leaderLines;
    public ElementID getTagId%28%29;
    public ElementID getRebarId%28%29;
}
/**
*@opt all
*@note RebarES
*/
class CRebarES {
    static public ElementIDs m_hostId;
    static public ElementID m_areaRebarId;
}
/**
*@opt all
*@note ExtesnionStorage
*/
class CAreaRebarES  extends CRebarES{
    static public ElementID m_plateId;
    static public ElementID m_areaRebarId;
    static public ElementIDs m_aroundRebarIds;
    public ElementID getAroundRebarIds%28%29;
    public ElementID setAroundRebarIds%28%29;
}
/**
*@opt all
*@note ExtesnionStorage2
*/
class CAdditionaRebarES  extends CRebarES{
    static public ElementID m_plateId;
    static public ElementID m_additionalRebarId;
}
)


![Alt text](https://g.gravizo.com/svg?
/**
*Structural Things
*@opt commentname
*@note Notes can
*be extended to
*span multiple lines
*/
class Structural{}
/**
*@opt all
*@note Class
*/
class Counter extends Structural {
    static public int counter;
    public int getCounter%28%29;
}
/**
*@opt shape activeclass
*@opt all
*@note Active Class
*/
class RunningCounter extends Counter{}
)
