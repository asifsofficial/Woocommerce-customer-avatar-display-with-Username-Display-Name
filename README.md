# Woocommerce customer avatar display with Username Display Name

## Location
```
function my_custom_account_avatar() {
    $current_user = wp_get_current_user();
    echo '<div class="my-custom-avatar">' . get_avatar( get_current_user_id(), 60, '', '', array('class' => 'avatar') );
    if ( isset( $current_user->display_name ) && ! empty( $current_user->display_name ) ) {
        echo '<div class="username">' . strtoupper(substr($current_user->display_name, 0, 15)) . '</div>';
    }else{
        echo '<div class="username">' . strtoupper(substr($current_user->user_login, 0, 15)) . '</div>';
    }
    echo '</div>';
}
add_action( 'woocommerce_before_account_navigation', 'my_custom_account_avatar' );
```

## Custom css
```
/* My account page custom CSS Start */
.my-custom-avatar {
	background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
	text-align: center; 
	background-image: url(/wp-content/uploads/2023/01/my-account-bg.webp); 
	margin-bottom: 15px; 
	border-radius: 8px; 
	padding: 15px;
	box-shadow: 0px 4px 8px 0px rgb(0 0 0 / 20%), 0 6px 20px 0 rgb(0 0 0 / 19%);
}

.my-custom-avatar img.avatar {
  border-radius: 50%;
  overflow: hidden;
  margin-right: 5px;
}

.username{
	display: inline-block;
	margin-left: 5px;
  font-size:16px;
  font-weight:bold;
  color: white;

}

.woocommerce-MyAccount-content>p {
  display: none;
}
```
