# queryDATA




import java.sql.*;
public class Main {
    public static void main(String[] args) {
        Connection con;
        String driver="com.mysql.jdbc.Driver";
        String url="jdbc:mysql://localhost:3306/test";
        String user="root";
        String password="root";
        try {
            Class.forName(driver);
            con = DriverManager.getConnection(url, user, password);
            if (!con.isClosed()) {
                System.out.println("数据库连接成功");
            }
            Statement statement = con.createStatement();
            String sql = "select * from goods;";
            ResultSet resultSet = statement.executeQuery(sql);
            String name;
            int price;
            while (resultSet.next()) {
                name = resultSet.getString("name");
                System.out.println("商品：" + name);
                price = resultSet.getInt("price");
                System.out.println("价格：" + price);
            }
            resultSet.close();
            con.close();
        } catch (ClassNotFoundException e) {
            System.out.println("数据库驱动没有安装");

        } catch (SQLException e) {
            System.out.println("数据库连接失败");
        }
    }
}


