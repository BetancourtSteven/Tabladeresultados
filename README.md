package application;
import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.ComboBox;
import javafx.scene.control.TableColumn;
import javafx.scene.control.TableView;
import javafx.scene.control.cell.PropertyValueFactory;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.HBox;
import javafx.scene.layout.VBox;
import javafx.scene.text.Text;
import javafx.stage.Stage;

public class Main extends Application {

    public static class Driver {
        private String driverName;
        private int wins;
        private int totalPoints;
        private int rank;

        public Driver(String driverName, int wins, int totalPoints, int rank) {
            this.driverName = driverName;
            this.wins = wins;
            this.totalPoints = totalPoints;
            this.rank = rank;
        }

        public String getDriverName() {
            return driverName;
        }

        public int getWins() {
            return wins;
        }

        public int getTotalPoints() {
            return totalPoints;
        }

        public int getRank() {
            return rank;
        }
    }

    @Override
    public void start(Stage primaryStage) {
        // Create the ComboBox
        Text yearLabel = new Text("Año:");
        ComboBox<String> yearComboBox = new ComboBox<>();
        yearComboBox.getItems().addAll("2016", "2017", "2018", "2019", "2020");
        yearComboBox.setValue("2016");

        // Create HBox to center the ComboBox
        HBox yearBox = new HBox(10);
        yearBox.setAlignment(Pos.CENTER);
        yearBox.getChildren().addAll(yearLabel, yearComboBox);

        // Create the TableView
        TableView<Driver> tableView = new TableView<>();

        TableColumn<Driver, String> driverNameColumn = new TableColumn<>("Driver Name");
        driverNameColumn.setCellValueFactory(new PropertyValueFactory<>("driverName"));

        TableColumn<Driver, Integer> winsColumn = new TableColumn<>("Wins");
        winsColumn.setCellValueFactory(new PropertyValueFactory<>("wins"));

        TableColumn<Driver, Integer> totalPointsColumn = new TableColumn<>("Total Points");
        totalPointsColumn.setCellValueFactory(new PropertyValueFactory<>("totalPoints"));

        TableColumn<Driver, Integer> rankColumn = new TableColumn<>("Rank");
        rankColumn.setCellValueFactory(new PropertyValueFactory<>("rank"));

        tableView.getColumns().add(driverNameColumn);
        tableView.getColumns().add(winsColumn);
        tableView.getColumns().add(totalPointsColumn);
        tableView.getColumns().add(rankColumn);

        // Add example data to the TableView
        tableView.getItems().add(new Driver("Lewis Hamilton", 10, 250, 1));
        tableView.getItems().add(new Driver("Sebastian Vettel", 8, 220, 2));

        // Create the layout and add the components
        VBox layout = new VBox(10);
        layout.setPadding(new Insets(10));
        layout.getChildren().addAll(tableView);

        BorderPane root = new BorderPane();
        root.setTop(yearBox);
        root.setCenter(layout);

        // Set up the scene and stage
        Scene scene = new Scene(root, 285, 400);
        primaryStage.setScene(scene);
        primaryStage.setTitle("TABLA DE RESULTADOS");
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}

![image](https://github.com/BetancourtSteven/Tabladeresultados/assets/169225554/89c92e09-c430-44a8-8926-4384be24bf88)
![image](https://github.com/BetancourtSteven/Tabladeresultados/assets/169225554/31e661d2-c35c-47a5-961a-d366ef82d0ad)

