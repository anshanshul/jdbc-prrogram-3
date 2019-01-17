# jdbc-prrogram-3
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectURL {
    public static void main(String[] args) {
    	//System.out.println("hello");
        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://OPTIMUS-75:1433;databaseName=train;user=sa;password=root";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT TOP 10 * FROM traindetails";
            ResultSet rs = stmt.executeQuery(SQL);
        	
            while(rs.next()){
                //Retrieve by column name
                int trainid  = rs.getInt("trainid");
                
                String first = rs.getString("trainid");
               
            
            
            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println(rs.getString("trainname"));
            System.out.println(rs.getString("trainid"));
            }
        }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
