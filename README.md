### 广播管理模块是发展性测评系统中的一个重要组成部分，提供了对校园内信息的快速发布和管理功能。用户可以方便地发布各类通知、公告、活动等信息，同时可以进行针对性推送，例如仅向某个班级或部门发布信息。这个模块可以极大地提高学校内部信息流通的速度和效率，并且有利于学校的日常管理和运营。

## The broadcast management module is an important part of the developmental assessment system, providing rapid dissemination and management of information on campus. Users can easily post various types of announcements, announcements, events, etc., and can also make targeted pushes, such as only releasing information to a certain class or department. This module can greatly improve the speed and efficiency of information flow within the school, and is conducive to the daily management and operation of the school.

### 具体的代码实现可以参考以下示例；
## For specific code implementation, refer to the following example.

package com.ruoyi.system.domain;

import javax.validation.constraints.NotBlank;

import javax.validation.constraints.Size;

import org.apache.commons.lang3.builder.ToStringBuilder;

import org.apache.commons.lang3.builder.ToStringStyle;

import com.ruoyi.common.core.domain.BaseEntity;

import com.ruoyi.common.xss.Xss;

/**
 * 通知公告表 sys_notice
 * 
 * @author ruoyi
 */
public class SysNotice extends BaseEntity
{
    private static final long serialVersionUID = 1L;

    /** 公告ID */
    private Long noticeId;

    /** 公告标题 */
    private String noticeTitle;

    /** 公告类型（1通知 2公告） */
    private String noticeType;

    /** 公告内容 */
    private String noticeContent;

    /** 公告状态（0正常 1关闭） */
    private String status;

    public Long getNoticeId()
    {
        return noticeId;
    }

    public void setNoticeId(Long noticeId)
    {
        this.noticeId = noticeId;
    }

    @Xss(message = "公告标题不能包含脚本字符")
    
    @NotBlank(message = "公告标题不能为空")
    
    @Size(min = 0, max = 50, message = "公告标题不能超过50个字符")
    
    public String getNoticeTitle()
    {
        return noticeTitle;
    }

    public void setNoticeTitle(String noticeTitle)
    {
        this.noticeTitle = noticeTitle;
    }

    public String getNoticeType()
    {
        return noticeType;
    }

    public void setNoticeType(String noticeType)
    {
        this.noticeType = noticeType;
    }

    public String getNoticeContent()
    {
        return noticeContent;
    }

    public void setNoticeContent(String noticeContent)
    {
        this.noticeContent = noticeContent;
    }

    public String getStatus()
    {
        return status;
    }

    public void setStatus(String status)
    {
        this.status = status;
    }

    @Override
    
    public String toString() {
    
        return new ToStringBuilder(this,ToStringStyle.MULTI_LINE_STYLE)
        
            .append("noticeId", getNoticeId())
            
            .append("noticeTitle", getNoticeTitle())
            
            .append("noticeType", getNoticeType())
            
            .append("noticeContent", getNoticeContent())
            
            .append("status", getStatus())
            
            .append("createBy", getCreateBy())
            
            .append("createTime", getCreateTime())
            
            .append("updateBy", getUpdateBy())
            
            .append("updateTime", getUpdateTime())
            
            .append("remark", getRemark())
            
            .toString();
    }
}

# <body>
  <header>
    <div class="logo">My Github Page</div>
    <nav>
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </nav>
  </header>
  <h1>Welcome to My Github Page</h1>
  <footer>&copy; 2023 My Github Page. All rights reserved.</footer>
</body>
</html>

