```json json_schema
{
  "type": "object",
  "title": "Handlebars Email Template Objects",
  "properties": {
    "Global Email Template Objects": {
      "description": "Data available across all email templates.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/global.yml"
        }
      ],
      "type": "object"
    },
    "Abandoned Cart Email Template Objects": {
      "description": "Data available to the abandoned cart email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/abandoned_cart_email.yml"
        }
      ],
      "type": "object"
    },
    "Account Settings Edited Email Template Objects": {
      "description": "Data available to the account details changed email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/account_details_changed_email.yml"
        }
      ],
      "type": "object"
    },
    "Password Reset Email Template Objects": {
      "title": "Account Reset Password Email Template",
      "description": "Data available to the reset password email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/account_reset_password_email.yml"
        }
      ],
      "type": "object"
    },
    "Order Status Update Email Template Objects": {
      "description": "Data available to the combined order status email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/combined_order_status_email.yml"
        }
      ],
      "type": "object"
    },
    "Account Created Email Template Objects": {
      "title": "Create Account Template",
      "description": "Data available to the create account email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/create_account_email.yml"
        }
      ],
      "type": "object"
    },
    "Account Created Guest Email Template Objects": {
      "title": "Create Guest Account Template",
      "description": "Data available to the create guest account email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/create_guest_account_email.yml"
        }
      ],
      "type": "object"
    },
    "Gift Certificate Recipient Email Template Objects": {
      "title": "Gift Certificate Email Template",
      "description": "Data available to the gift certificate email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/gift_certificate_email.yml"
        }
      ],
      "type": "object"
    },
    "Order Email Template Objects": {
      "description": "Data available to the invoice email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/invoice_email.yml"
        }
      ],
      "type": "object"
    },
    "Order Notification Email Template Objects": {
      "description": "Data available to the order message notification email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/order_message_notification.yml"
        }
      ],
      "type": "object"
    },
    "Sign-in Link Request Email Template Objects": {
      "description": "Data available to the passwordless login email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/passwordless_login_email.yml"
        }
      ],
      "type": "object"
    },
    "Product Review Request Email Template Objects": {
      "title": "Product Review Email Template",
      "description": "Data available to the product review email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/product_review_email.yml"
        }
      ],
      "type": "object"
    },
    "Return Approved Email Template Objects": {
      "description": "Data available to the return confirmation email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/return_confirmation_email.yml"
        }
      ],
      "type": "object"
    },
    "Return Status Change Email Template Objects": {
      "description": "Data available to the return status change email template.",
      "allOf": [
        {
          "$ref": "https://raw.githubusercontent.com/bigcommerce/api-specs/master/models/email_templates/return_status_change_email.yml"
        }
      ],
      "type": "object"
    }
  }
}
```
