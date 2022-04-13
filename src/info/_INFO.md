# Updating your restaurant's info guide

## File: general.json

In the general.json file you can update general information regarding your restaurant, including:

- `name`
    - Your restaurant's name.
    - Put your restaurant's name in apostrophes.
        - E.g.
        > `"name": "McRestaurant Burgers"`
- `phonenumber`
    - Your restaurant's phone number.
    - 10 digits. No space. 
        - E.g.
        > `"phonenumber": "6049997777"`
- `address`
    - Your restaurant's address.
    - Put your restaurant's address in apostrophes.
        - E.g.
        > `"address": "0101 General Street. Vancouver, BC. V0V 0V0"`
- `hours`
    - Your restaurant's opening and closing hours.
    - Format in 24 hour time. The first 2 digits are the hour and the last 2 digits are the minute.
        - E.g. `0730` is 7:30 AM and `2200` is 10:00 PM.
        > `"sunday opening": 0730`
        > `"sunday closing": 2200`
- `takeout`
    - Does your restaurant offer takeout?
    - Put `true` (for yes) or `false` (for no)
        - E.g.
        > `"takeout": true`
- `delivery`
    - Does your restaurant offer its own delivery?
    - Put `true` (for yes) or `false` (for no)
        - E.g.
        > `"delivery": false`
- `payment`
    - The payment types your restaurant accepts.
    - For each payment type, put either `true` or `false` to indicate whether your restaurant accepts that type of payment.
        - E.g. 
        > `"interac": true`
        >
        > `"mastercard": false`
- `socialmedia`
    - Links to your restaurant's social media.
    - For each, put the link to that social media in apostrophes. If you don't have a social media, simply leave it blank (`""`). 
        - E.g. 
        > `"facebook": "www.facebook.com/your_restaurant"`
        >
        > `"kik": ""`

_________________

## File: menu.json

In the menu.json file you can update information regarding your restaurant's menu. This section is fully customizable. 

- First, you can create **menu categories**.
    - You can create as many or as few as you'd like.
    - The format is as follows:
        ```
        {
            "shortname": {
                "name": "Category Name",
                "desc": "Description of category",
                "menu" {
                    [individual items will go here]
                }
            }
        }
        ```
        - `shortname` 
            - A short name for your custom fee.
        - `name`
            - The name to be displayed for your category.
            - Put the name in apostrophes.
                - E.g.
                > `"name": "Burger Meals"`
        - `desc`
            - The description to be displayed for your category.
            - Put the description in apostrophes.
                - E.g.
                > `"desc": "The comforting taste of a juicy and delicious 100% Canadian beef burger."`
- Second, you can create **individual items** for your menu categories.
    - You can create as many or as few as you'd like.
    - The format is as follows:
        ```
        "shortname": {
            "name": "Item Name",
            "price": 10.99,
            "desc": "Description of item.",
            "options": {
                [item options will go here]
            }
        }
        ```
        - `shortname` 
                - A short name for your custom fee.
        - `name`
            - The name to be displayed for your item.
            - Put the name in apostrophes.
                - E.g.
                > `"name": "Burger with Cheese"`
        - `price`
            - The price for your item.
            - Put your price in dollar ammount.
                - E.g.
                > `"price": 10.99`
        - `desc`
            - The description to be displayed for your item.
            - Put the description in apostrophes.
                - E.g.
                > `"desc": "Our simple, classic cheeseburger begins with a 100% pure beef burger seasoned with just a pinch of salt and pepper."`
- Third, you can create **item options** for your items.
    - You can create as many or as few as you'd like.
    - The format is as follows:
        - **Option Type 1**: single-select option. (Radio)
            ```
            "shortname": {
                "name": "Option Name",
                "type": 1,
                "choices": ["Choice 1", "Choice 2"],
                "prices": [0, 0.5],
                "isrequired": true
            }
            ```
            - `type`
                - The option type for your option. In this case for a single-select option, it's `1`.
                - By default, it's set so the user must choose one option and only one.
            - `choices`
                - A list of option choices.
                - Within the square brackets, list your items in order.
                    - E.g.
                    > `"choices": ["Small", "Medium", "Large"]`
            - `prices`
                - If your options have additional prices.
                - Within the square brackets, list your item prices in order matching the `choices` list. If your option doesn't have a price, simply put it as `0`. 
                    - E.g.
                    > `"prices": [0, 0.5, 0.8]`
            - `isrequired`
                - Whether or not your option is required to be answered.
                - Put `true` (for yes) or `false` (for no) 
                    - E.g.
                    > `"isrequired": true`
        - **Option Type 2**: multi-select option. (Checkbox)
            ```
            "shortname": {
                "name": "Option Name",
                "type": 2,
                "choices": ["Choice 1", "Choice 2", "Choice 3"],
                "prices": [0.5, 0.5, 0.5],
                "min": 1,
                "max": 2,
                "isrequired": true
            }
            ```
            - `type`
                - The option type for your option. In this case for a single-select option, it's `2`.
            - `min`
                - The minimum amount of options selected. Only applies for Option Types 2 and 3.
                - Put a whole number.
                    - E.g.
                    > `"min": 1`
                    - In this case, the user must choose at least `1` of the options provided.
            - `max`
                - The maximum amount of options selected. Only applies for Option Types 2 and 3.
                - Put a whole number.
                    - E.g.
                    > `"max": 2`
                    - In this case, the user must choose `2` or less of the options provided.
        - **Option Type 3**: counter-select option.
            ```
            "shortname": {
                "name": "Option Name",
                "type": 3,
                "choices": ["Choice 1", "Choice 2", "Choice 3"],
                "prices": [0.5, 0.5, 0.5],
                "initial": [1, 2, 0],
                "min": 1,
                "max": 4,
                "isrequired": true
            }
            ```
            - `type`
                - The option type for your option. In this case for a single-select option, it's `3`.
            - `initial`
                - The initial amount of that option choice. Only applies for Option Type 3.
                - Within the square brackets, put a whole number for each option choice in order matching the `choices` list.
                    - E.g.
                    > `"initial": [1, 2, 0]`
                    - In this case, the counters start with `1` for Choice 1 and `2` for Choice 2 and `0` for Choice 3.
            - `min`
                - The minimum amount of options selected. Only applies for Option Types 2 and 3.
                - Put a whole number.
                    - E.g.
                    > `"min": 1`
                    - In this case, the counters total must be at least `1`.
            - `max`
                - The maximum amount of options selected. Only applies for Option Types 2 and 3.
                - Put a whole number.
                    - E.g.
                    > `"max": 4`
                    - In this case, the counters total must be `4` or less.

_________________

## File: payment.json

In the payment.json file you can update information regarding your restaurant's payments, including:

- `deliveryfee`
    - Your restaurant's delivery fee per kilometres.
        - If you do not do delivery, simply put `0` for the fee.
    - Put the dollar amount per kilometres.
        - E.g. `0.25` would be 25 cents per kilometres.
        > `"deliveryfee": 0.25`
- `customfees`
    - This section is special in which you can create your own fees.
    - You can create as many or as few as you'd like.
    - The format is as follows:
        ```
        "customfees": {
            "shortname": {
                "name": "Name",
                "type": "percentage",
                "fee": 2
            }
        }
        ```
    - `shortname` 
        - A short name for your custom fee.
    - `name`
        - The name to be displayed for your custom fee.
        - Put the name in apostrophes.
            - E.g.
            > `"name": "Plastic Bag Fee"`
    - `type`
        - The fee type for your custom fee.
        - Either `"percentage"` (charge a percentage of the order subtotal) or `"flat"` (charge a flat fee for the order)
            - E.g.
            > `"type": "flat"`
    - `fee`
        - The fee for your custom fee.
        - Put your fee in dollar ammount.
            - E.g.
            > `"fee": 2`
            - If you put `"percentage"` for the type, a fee of `2%` would be charged for the order.
            - If you put `"flat"` for the type, a fee of `$2` would be charged for the order.