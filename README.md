### 具体的代码实现可以参考以下示例；For specific code implementation, refer to the following example.

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.PreparedStatement;

import java.sql.ResultSet;

import java.sql.SQLException;


public class Broadcast {
    private int id;
    private String sender;
    private String receiver;
    private String content;
    private String date;

    // 构造函数
    public Broadcast(int id, String sender, String receiver, String content, String date) {
        this.id = id;
        this.sender = sender;
        this.receiver = receiver;
        this.content = content;
        this.date = date;
    }

    // 发送广播
    public static void sendBroadcast(Broadcast broadcast) {
        Connection conn = null;
        PreparedStatement pstmt = null;

        try {
            // 连接数据库
            conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

            // 拼接 SQL 语句
            String sql = "INSERT INTO broadcasts(sender, receiver, content, date) VALUES (?, ?, ?, ?)";
            pstmt = conn.prepareStatement(sql);

            // 设置参数
            pstmt.setString(1, broadcast.getSender());
            pstmt.setString(2, broadcast.getReceiver());
            pstmt.setString(3, broadcast.getContent());
            pstmt.setString(4, broadcast.getDate());

            // 执行 SQL 语句
            pstmt.executeUpdate();

            System.out.println("发送广播成功！");
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            // 关闭连接
            try {
                if (pstmt != null) pstmt.close();
                if (conn != null) conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

    // 查看所有广播
    public static Broadcast[] getAllBroadcasts() {
        Connection conn = null;
        PreparedStatement pstmt = null;
        ResultSet rs = null;
        Broadcast[] broadcasts = null;

        try {
            // 连接数据库
            conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

            // 拼接 SQL 语句
            String sql = "SELECT * FROM broadcasts";
            pstmt = conn.prepareStatement(sql);
            rs = pstmt.executeQuery();

            // 获取广播个数
            rs.last();
            int numRows = rs.getRow();
            broadcasts = new Broadcast[numRows];
            rs.beforeFirst();

            // 解析查询结果
            int i = 0;
            while (rs.next()) {
                int id = rs.getInt("id");
                String sender = rs.getString("sender");
                String receiver = rs.getString("receiver");
                String content = rs.getString("content");
                String date = rs.getString("date");

                Broadcast broadcast = new Broadcast(id, sender, receiver, content, date);
                broadcasts[i] = broadcast;
                i++;
            }
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            // 关闭连接
            try {
                if (rs != null) rs.close();
                if (pstmt != null) pstmt.close();
                if (conn != null) conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }

        return broadcasts;
    }

    // 删除广播
    public static void deleteBroadcast(int id) {
        Connection conn = null;
        PreparedStatement pstmt = null;

        try {
            // 连接数据库
            conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

            // 拼接 SQL 语句
            String sql = "DELETE FROM broadcasts WHERE id=?";
            pstmt = conn.prepareStatement(sql);

            // 设置参数
            pstmt.setInt(1, id);

            // 执行 SQL 语句
            pstmt.executeUpdate();

            System.out.println("删除广播成功！");
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            // 关闭连接
            try {
                if (pstmt != null) pstmt.close();
                if (conn != null) conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

    // getters and setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getSender() {
        return sender;
    }

    public void setSender(String sender) {
        this.sender = sender;
    }

    public String getReceiver() {
        return receiver;
    }

    public void setReceiver(String receiver) {
        this.receiver = receiver;
    }

    public String getContent() {
        return content;
    }

    public void setContent(String content) {
        this.content = content;
    }

    public String getDate() {
        return date;
    }

    public void setDate(String date) {
        this.date = date;
    }
}

<body>
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

