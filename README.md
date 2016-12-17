## Installation

### Step 1

Place `login-caldera.php` into plugin directory.

### Step 2

Add these lines into the configuration of `wp-oauth.php`:

		'wpoa_caldera_api_enabled' => 0,								// 0, 1
		'wpoa_caldera_api_id' => '',									// any string
		'wpoa_caldera_api_secret' => '',								// any string
		
### Step 3

Place this snippet in `wp-oauth-settings.php`:

			<!-- START Login with Caldera section -->
			<div id="wpoa-settings-section-login-with-caldera" class="wpoa-settings-section">
			<h3>Login with Caldera</h3>
			<div class='form-padding'>
			<table class='form-table'>
				<tr valign='top'>
				<th scope='row'>Enabled:</th>
				<td>
					<input type='checkbox' name='wpoa_caldera_api_enabled' value='1' <?php checked(get_option('wpoa_caldera_api_enabled') == 1); ?> />
				</td>
				</tr>
				
				<tr valign='top'>
				<th scope='row'>App ID:</th>
				<td>
					<input type='text' name='wpoa_caldera_api_id' value='<?php echo get_option('wpoa_caldera_api_id'); ?>' />
				</td>
				</tr>
				 
				<tr valign='top'>
				<th scope='row'>App Secret:</th>
				<td>
					<input type='text' name='wpoa_caldera_api_secret' value='<?php echo get_option('wpoa_caldera_api_secret'); ?>' />
				</td>
				</tr>
			</table> <!-- .form-table -->
			<?php submit_button('Save all settings'); ?>
			</div> <!-- .form-padding -->
			</div> <!-- .wpoa-settings-section -->
			<!-- END Login with Caldera section -->

### Step 4

Open `wp-oauth.php` and insert around line 710:

		$html .= $this->wpoa_login_button("caldera", "Caldera", $atts);