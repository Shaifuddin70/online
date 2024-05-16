<?php
include("../connection/connect.php");
error_reporting(0);
session_start();
?>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="">
    <meta name="author" content="">
    <link rel="icon" type="image/png" sizes="16x16" href="images/favicon.png">
    <title>All Orders</title>
    <link href="css/lib/bootstrap/bootstrap.min.css" rel="stylesheet">
    <link href="css/helper.css" rel="stylesheet">
    <link href="css/style.css" rel="stylesheet">
</head>

<body class="fix-header fix-sidebar">
    <div class="preloader">
        <svg class="circular" viewBox="25 25 50 50">
            <circle class="path" cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10" />
        </svg>
    </div>

    <div id="main-wrapper">

        <div class="header">
            <nav class="navbar top-navbar navbar-expand-md navbar-light">
                <div class="navbar-header">
                    <a class="navbar-brand" href="dashboard.php">

                        <span><img src="images/icn.png" alt="homepage" class="dark-logo" /></span>
                    </a>
                </div>
                <div class="navbar-collapse">

                    <ul class="navbar-nav mr-auto mt-md-0">




                    </ul>

                    <ul class="navbar-nav my-lg-0">



                        <li class="nav-item dropdown">

                            <div class="dropdown-menu dropdown-menu-right mailbox animated zoomIn">
                                <ul>
                                    <li>
                                        <div class="drop-title">Notifications</div>
                                    </li>

                                    <li>
                                        <a class="nav-link text-center" href="javascript:void(0);"> <strong>Check all notifications</strong> <i class="fa fa-angle-right"></i> </a>
                                    </li>
                                </ul>
                            </div>
                        </li>

                        <li class="nav-item dropdown">
                            <a class="nav-link dropdown-toggle text-muted  " href="#" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"><img src="images/bookingSystem/user-icn.png" alt="user" class="profile-pic" /></a>
                            <div class="dropdown-menu dropdown-menu-right animated zoomIn">
                                <ul class="dropdown-user">
                                    <li><a href="logout.php"><i class="fa fa-power-off"></i> Logout</a></li>
                                </ul>
                            </div>
                        </li>
                    </ul>
                </div>
            </nav>
        </div>

        <div class="left-sidebar">

            <div class="scroll-sidebar">

                <nav class="sidebar-nav">
                    <ul id="sidebarnav">
                        <li class="nav-devider"></li>
                        <li class="nav-label">Home</li>
                        <li> <a href="dashboard.php"><i class="fa fa-tachometer"></i><span>Dashboard</span></a></li>
                        <li class="nav-label">Log</li>
                        <li> <a href="all_users.php"> <span><i class="fa fa-user f-s-20 "></i></span><span>Users</span></a></li>
                        <li> <a class="has-arrow  " href="#" aria-expanded="false"><i class="fa fa-archive f-s-20 color-warning"></i><span class="hide-menu">Restaurant</span></a>
                            <ul aria-expanded="false" class="collapse">
                                <li><a href="all_restaurant.php">All Restaurants</a></li>
                                <li><a href="add_category.php">Add Category</a></li>
                                <li><a href="add_restaurant.php">Add Restaurant</a></li>

                            </ul>
                        </li>
                        <li> <a class="has-arrow  " href="#" aria-expanded="false"><i class="fa fa-cutlery" aria-hidden="true"></i><span class="hide-menu">Menu</span></a>
                            <ul aria-expanded="false" class="collapse">
                                <li><a href="all_menu.php">All Menues</a></li>
                                <li><a href="add_menu.php">Add Menu</a></li>


                            </ul>
                        </li>
                        <li> <a href="all_orders.php"><i class="fa fa-shopping-cart" aria-hidden="true"></i><span>Orders</span></a></li>

                    </ul>
                </nav>

            </div>

        </div>

        <div class="page-wrapper">
            <div class="container-fluid">
                <div class="row">
                    <div class="col-12">
                        <div class="col-lg-12">
                            <div class="card card-outline-primary">
                                <div class="card-header">
                                    <h4 class="m-b-0 text-white">All Orders</h4>
                                </div>
                                <!-- Filter form -->
                                <div class="row">
                                    <div class="col-md-6">
                                        <form action="" method="GET">
                                            <div class="form-group">
                                                <label for="start_date">Start Date:</label>
                                                <input type="date" class="form-control" id="start_date" name="start_date">
                                            </div>
                                            <div class="form-group">
                                                <label for="end_date">End Date:</label>
                                                <input type="date" class="form-control" id="end_date" name="end_date">
                                            </div>
                                            <button type="submit" class="btn btn-primary">Filter</button>
                                        </form>
                                    </div>
                                    <div class="col-md-6">
                                        <form action="" method="GET">
                                            <div class="form-group">
                                                <label for="restaurant">Select Restaurant:</label>
                                                <select class="form-control" id="restaurant" name="restaurant">
                                                    <option value="">All Restaurants</option>
                                                    <?php
                                                    // Fetch restaurant data from your database
                                                    $restaurant_query = mysqli_query($db, "SELECT * FROM restaurant");
                                                    while ($restaurant_row = mysqli_fetch_assoc($restaurant_query)) {
                                                        // Output each restaurant as an option
                                                        echo "<option value='{$restaurant_row['rs_id']}'>{$restaurant_row['title']}</option>";
                                                    }
                                                    ?>
                                                </select>
                                            </div>
                                            <button type="submit" class="btn btn-primary">Filter</button>
                                        </form>
                                        
                                    </div>
                                </div>
                                <!-- Orders table -->
                                <div class="table-responsive m-t-40">
                                    <table id="myTable" class="table table-bordered table-striped">
                                        <thead class="thead-dark">
                                            <tr>
                                                <th>S/N</th>
                                                <th>User</th>
                                                <th>Restaurant</th>
                                                <th>Title</th>
                                                <th>Quantity</th>
                                                <th>Price</th>
                                                <th>Status</th>
                                                <th>Reg-Date</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <?php



                                            // Start date and end date filter
                                            $start_date = isset($_GET['start_date']) ? $_GET['start_date'] : null;
                                            $end_date = isset($_GET['end_date']) ? $_GET['end_date'] : null;

                                            // Restaurant filter
                                            $restaurant_id = isset($_GET['restaurant']) ? $_GET['restaurant'] : null;

                                            $sql = "SELECT users.username, restaurant.title AS restaurant_title, users_orders.* FROM users_orders 
                                                    INNER JOIN users ON users.u_id = users_orders.u_id
                                                    INNER JOIN restaurant ON restaurant.rs_id = users_orders.rs_id";

                                            // Apply date range filter
                                            // Apply date range filter
                                            if ($start_date && $end_date) {
                                                // Convert the start and end dates to the correct format
                                                $start_date_formatted = date("Y-m-d", strtotime($start_date));
                                                $end_date_formatted = date("Y-m-d", strtotime($end_date));

                                                // Add the date filter to the SQL query
                                                $sql .= " WHERE DATE(users_orders.date) BETWEEN '$start_date_formatted' AND '$end_date_formatted'";
                                            }


                                            // Apply restaurant filter
                                            if ($restaurant_id) {
                                                if (strpos($sql, 'WHERE') !== false) {
                                                    $sql .= " AND users_orders.rs_id = '$restaurant_id'";
                                                } else {
                                                    $sql .= " WHERE users_orders.rs_id = '$restaurant_id'";
                                                }
                                            }
$c=1;

                                            $query = mysqli_query($db, $sql);

                                            if (mysqli_num_rows($query) > 0) {
                                                while ($row = mysqli_fetch_assoc($query)) {
                                                    // Display order details
                                                    echo "<tr>";
                                                    echo "<td>$c</td>";
                                                    echo "<td>{$row['username']}</td>";
                                                    echo "<td>{$row['restaurant_title']}</td>";
                                                    echo "<td>{$row['title']}</td>";
                                                    echo "<td>{$row['quantity']}</td>";
                                                    echo "<td>{$row['price']}</td>";
                                                    echo "<td>{$row['status']}</td>";
                                                    echo "<td>{$row['date']}</td>";
                                                    echo "</tr>";
                                                    $c++;
                                                }
                                            } else {
                                                echo '<tr><td colspan="7"><center>No Orders</center></td></tr>';
                                            }
                                            ?>
                                        </tbody>
                                    </table>
                                    <span id="totalPrice"></span>
                                    <span id="totalOrders"></span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <footer class="footer"> © 2024 - Online Food Ordering System</footer>
        </div>
    </div>

    <script src="js/lib/jquery/jquery.min.js"></script>
    <script src="js/lib/bootstrap/js/popper.min.js"></script>
    <script src="js/lib/bootstrap/js/bootstrap.min.js"></script>
    <script src="js/jquery.slimscroll.js"></script>
    <script src="js/sidebarmenu.js"></script>
    <script src="js/lib/sticky-kit-master/dist/sticky-kit.min.js"></script>
    <script src="js/custom.min.js"></script>
    <script src="js/lib/datatables/datatables.min.js"></script>
    <script src="js/lib/datatables/cdn.datatables.net/buttons/1.2.2/js/dataTables.buttons.min.js"></script>
    <script src="js/lib/datatables/cdn.datatables.net/buttons/1.2.2/js/buttons.flash.min.js"></script>
    <script src="js/lib/datatables/cdnjs.cloudflare.com/ajax/libs/jszip/2.5.0/jszip.min.js"></script>
    <script src="js/lib/datatables/cdn.rawgit.com/bpampuch/pdfmake/0.1.18/build/pdfmake.min.js"></script>
    <script src="js/lib/datatables/cdn.rawgit.com/bpampuch/pdfmake/0.1.18/build/vfs_fonts.js"></script>
    <script src="js/lib/datatables/cdn.datatables.net/buttons/1.2.2/js/buttons.html5.min.js"></script>
    <script src="js/lib/datatables/cdn.datatables.net/buttons/1.2.2/js/buttons.print.min.js"></script>
    <script>
    // Function to calculate total price and total number of orders
    function calculateTotals() {
        var totalPrice = 0;
        var totalOrders = 0;
        // Loop through each row in the table
        $('#myTable tbody tr').each(function() {
            // Extract the quantity and price from the current row
            var quantity = parseInt($(this).find('td:eq(4)').text()); // Corrected index for quantity
            console.log('Quantity:', quantity); // Log the quantity value to debug
            var price = parseFloat($(this).find('td:eq(5)').text());
            // Calculate the total price and total orders
            totalPrice += price;
            totalOrders += quantity;
        });
        // Display the total price and total orders in the designated spans
        $('#totalPrice').text('Total Price: ' + totalPrice.toFixed(2));
        $('#totalOrders').text('Total Orders: ' + totalOrders);
    }

    // Call the function when the page loads and whenever the filter changes
    $(document).ready(function() {
        calculateTotals();

        // Trigger the calculation when the filter form is submitted
        $('form').submit(function() {
            calculateTotals();
        });

        // Trigger the calculation when the start date or end date changes
        $('#start_date, #end_date').change(function() {
            calculateTotals();
        });

        // Trigger the calculation when the restaurant filter changes
        $('#restaurant').change(function() {
            calculateTotals();
        });
    });
</script>




</body>

</html>