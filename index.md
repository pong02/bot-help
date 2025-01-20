# AA Personal Assistant

Welcome to the **AA Personal Assistant Bot**! Waltuh helps you manage your inventory of envelopes and stamps, track usage, and register groups for automated updates. Below you'll find detailed instructions for how to interact with the bot.

## Table of Contents
- [Features](#features)
- [Meta Commands](#meta-commands)
  - [`/ping`](#ping)
  - [`/list-groups`](#list-groups)
  - [`/register <group_numbers>`](#register-group_numbers)
  - [`/ocr-register <group_numbers>`](#ocr-register-group_numbers)
  - [`/list-registered`](#list-registered)
  - [`/deregister <group_numbers>`](#deregister-group_numbers)
  - [`/ocr-list`](#ocr-list)
  - [`/ocr-deregister <group_numbers>`](#ocr-deregister-group_numbers)
- [Inventory Management](#inventory-management)
  - [`/add-envelopes`](#add-envelopes)
  - [`/add-stamps`](#add-stamps)
  - [`/inventory`](#inventory)
  - [`/add-prices`](#add-prices)
  - [`/buy`](#buy)
  - [`/prices`](#prices)
- [Usage Tracking](#usage-tracking)
  - [`/estimated-usage`](#estimated-usage)
- [Automated Label Matching](#automated-label-matching)
  - [`/ocr-reference`](#ocr-reference)
  - [`/ocr-start`](#ocr-start)
  - [`/ocr-end`](#ocr-end)
- [How It Works](#how-it-works)
- [Notes](#notes)

## Features
- Manage envelope and stamp inventories with ease.
- Track usage of envelopes and stamps for different tasks.
- Register groups to control bot interactions.
- View and update inventory in real time.
- Use OCR to manage unfulfillable orders

---

## Commands

### **Meta Commands**

#### **`/ping`**
- **Description:** Checks if the bot is active and responsive.
- **Input:**  
    ```
    /ping
    ```
- **Response:**  
    ```
    ok
    ```

#### **`/list-groups`**
- **Description:** Lists all WhatsApp groups the bot is a part of.
- **Input:**  
    ```
    /list-groups
    ```
- **Response:**  
    A list of group names the bot is part of, formatted like:
  
    ```
    1. Group Name 1
    2. Group Name 2
    3. Group Name 3
    ```
    
#### **`/register <group_numbers>`**
- **Description:** Registers specific groups for bot interaction. You must replace `<group_numbers>` with a comma-separated list of group numbers from the `/list-groups` command. Only registered groups can interact with the bot for restricted commands.
- **Input:**  
    Example:
    ```
    /register 1, 3
    ```
    This will register Group 1 and Group 3 for interaction with the bot.

- **Response:**  
    The bot will send a message like:
    ```
    Registered Groups:
    - Group Name 1
    - Group Name 3
    ```   

#### **`/ocr-register <group_numbers>`**
- **Description:** Registers specific groups for bot *OCR* interaction. You must replace `<group_numbers>` with a comma-separated list of group numbers from the `/list-groups` command. Only OCR registered groups can use send images to the bot for OCR.
- **Input:**  
    Example:
    ```
    /ocr-register 1, 3
    ```
    This will register Group 1 and Group 3 for interaction with the bot.

- **Response:**  
    The bot will send a message like:
    ```
    Registered Groups:
    - Group Name 1
    - Group Name 3
    ```

#### **`/list-registered`**
- **Description:** Lists all the groups that have been registered for bot interaction.
- **Input:**  
    ```
    /list-registered
    ```
- **Response:**  
    A list of all registered group names, such as:
  
    ```
    Registered Groups:
    - Group Name 1
    - Group Name 3
    ```
    
#### **`/deregister <group_numbers>`**
- **Description:** Deregisters specific groups for bot interaction. You must replace `<group_numbers>` with a comma-separated list of group numbers from the `/list-registered` command. Deregistered groups can no longer interact with the bot for restricted commands.
- **Input:**  
    Example:
    ```
    /deregister 1, 3
    ```
    This will deregister Group 1 and Group 3 for interaction with the bot.
    
#### **`/ocr-list`**
- **Description:** Lists all the groups that have been registered for bot *OCR* interaction.
- **Input:**  
    ```
    /ocr-list
    ```
- **Response:**  
    A list of all OCR registered group names, such as:
  
    ```
    Registered Groups:
    - Group Name 1
    - Group Name 3
    ```
    
#### **`/ocr-deregister <group_numbers>`**
- **Description:** Deregisters specific groups for bot *OCR* interaction. You must replace `<group_numbers>` with a comma-separated list of group numbers from the `/ocr-list` command. Deregistered groups can no longer use the bot's OCR capabilities.
- **Input:**  
    Example:
    ```
    /deregister 1, 3
    ```
    This will deregister Group 1 and Group 3 for image interaction with the bot.
    
---

### **Inventory Management**

#### **`/add-envelopes`**
- **Description:** Adds envelopes to the inventory. You must provide the envelope type and quantity in the format: `<envelope_type>: <quantity>`. If an envelope type doesn't exist, it will be created.
- **Input:**  
    Example:
    ```
    /add-envelopes
    EnvelopeType1: 50
    EnvelopeType2: 100
    EnvelopeType3: 20
    ```
    This will add 50 of `EnvelopeType1`, 100 of `EnvelopeType2`, and 20 of `EnvelopeType3` to the inventory.

- **Response:**  
    The bot will confirm the additions like:
    ```
    Envelope Addition Results:
    EnvelopeType1: Added 50, New Total: 50
    EnvelopeType2: Added 100, New Total: 100
    EnvelopeType3: Added 20, New Total: 20
    ```

#### **`/add-stamps`**
- **Description:** Adds stamps to the inventory. You must provide the stamp type and quantity in the format: `<stamp_type>: <quantity>`. If a stamp type doesn't exist, it will be created.
- **Input:**  
    Example:
    ```
    /add-stamps
    StampTypeA: 200
    StampTypeB: 150
    ```
    This will add 200 of `StampTypeA` and 150 of `StampTypeB` to the stamp inventory.

- **Response:**  
    The bot will confirm the additions like:
    ```
    Stamp Addition Results:
    StampTypeA: Added 200, New Total: 200
    StampTypeB: Added 150, New Total: 150
    ```

---

#### **`/inventory`**
- **Description:** Shows the current inventory.

- **Response:**  
    The bot will show the envelope and stamp remaining like:
    ```
    Inventory:
    EnvelopeType1: 33
    EnvelopeType2: 92
    EnvelopeType3: 27
    EnvelopeType4: 0

    Stamp:
    StampTypeA: 93
    ```
---

#### **`/add-prices`**
- **Description:** Adds a new price entry. You must provide the stamp/envelope type and UNIT price in the format: `<item>: <price>`. If an item doesn't exist, it will be created.
- **Input:**  
    Example:
    ```
    /add-prices
    ExistingStampTypeA: 0.50
    NewStampTypeB: 0.30
    ExistingEnvelopeA: 0.31
    ExistingEnvelopeB: 9.94
    ```
    This will add a new item `NewStampTypeB` and update `StampTypeA`, `EnvelopeA`, `EnvelopeB` to the price json.

- **Response:**  
    The bot will confirm the additions like:
    ```
    Price Updates:
    Parcel-ExLarge: Updated to 0.5
    Small: Added new price for Small at 0.45
    ```

---

#### **`/buy`**
- **Description:** Calculates the total price for purchasing. You must provide the item and quantity in the format: `<item>: <quantity>`. If an item doesn't exist, it will be ignored.
- **Input:**  
    Example:
    ```
    /buy
    TMP-C5: 38
    Express: 44
    TMP-Large: 38
    FakeEnvelope: 98
    Satchel: 6
    Parcel-Medium: 3
    ```
    This will add 200 of `StampTypeA` and 150 of `StampTypeB` to the stamp inventory.

- **Response:**  
    The bot will calculate the price like:
    ```
    Purchase Summary:
    TMP-C5: 38 * 5.7 = 216.60
    Express: 44 * 8 = 352.00
    TMP-Large: 38 * 7.3 = 277.40
    FakeEnvelope: Not found
    Satchel: 6 * 9.41 = 56.46
    Parcel-Medium: 3 * 0.21 = 0.63
    Total: 903.09
    ```

---

#### **`/prices`**
- **Description:** Shows the current price list.

- **Response:**  
    The bot will show the envelope and stamp prices like:
    ```
    150c: 1.50
    TMP-Small: 5
    TMP-C5: 6
    TMP-Large: 8
    Express: 9
    Satchel: 10
    Parcel-Medium: 2
    Parcel-ExLarge: 3.5
    Small: 0.8
    ```
---


### **Usage Tracking**

#### **`/estimated-usage`**
- **Description:** Tracks and calculates the usage of envelopes and stamps. You must provide the envelope type and the number of envelopes used in the format: `<envelope_type>: <quantity>`. The bot will calculate how many stamps are needed for the specified number of envelopes and update both the envelope and stamp inventory.
- **Input:**  
    Example:
    ```
    /estimated-usage
    EnvelopeType1: 10
    EnvelopeType2: 5
    ```
    This will calculate the usage of 10 `EnvelopeType1` and 5 `EnvelopeType2` envelopes, and it will check how many stamps are needed for these quantities based on predefined stamp requirements.

- **Response:**  
    The bot will display a detailed response like:
    ```
    Inventory Changes:
    EnvelopeType1: Updated balance to 40
    EnvelopeType2: Updated balance to 95

    Stamp Changes:
    StampTypeA: 100 used for EnvelopeType1
    StampTypeB: 50 used for EnvelopeType2
    ```

---

### **Automated Label Matching**

#### **`/ocr-reference`**
- **Description:** Allows the upload of a single label information csv to match since the label printing is NOT always reliable. This ensures that the OCR result will only output what we printed. This is optional, so if this command is not run, OCR will still work as usual, just with 0% confidence at all times due to missing reference.
- **Input:**  
    Example:
    ```
    /ocr-reference
    ```
    This command will make the bot prompt for a CSV file. Please make sure the subsequent message is a `.csv`. If it is rejected, redo the command. Also please make sure there is NO caption under the file when uploading it to the bot. 

#### **`/ocr-start`**
- **Description:** This command will instruct the bot to start listening to images. Otherwise it will ignore. Each successful image upload will have OCR done, and immediately returned in the bot response. If matched with reference, it will return the label ROW in the reference excel while appending the matched row to the result csv, else, it will return whatever it read from the label for manual intervention. This is all in accordance to the CONFIDENCE output by the matching algorithm (as of time of writing, 75% confidence is automatically entered into result csv)
- **Input:**  
    Example:
    Once OCR has started and an image is detected...

- **Response:**  
    The bot will display a detailed response like:
    - Met threshold
    ```
    Matched Row:
    23-12534-78169, Mark Wright, 9 Wright Av., Sheraton, VIC, 3630, [SP]/[C5] Z3-06-09 x1, 1
    Confidence: 84.93%
    ```
    
    - Failed to meet threshold:
    ```
    Matched Row with Low Confidence value, Review required:
    C-123817-A, John Cena, Deep Sea Ave., Bilgewater, FIS, 8312, [NG]/[C4] A1-10-12 x4, 1
    Confidence: 60.87%
    ```
    
    - No reference:
    ```
    No reference data available. Please upload reference data.
    Read label:
    george washington
    3200 Mount Vernon Memorial Highway, Mount Vernon, Virginia, 22121
    [SP]/[TMP-C5] D0-02-07 *1
    Confidence: 0%
    ```

#### **`/ocr-end`**
- **Description:** Collects all the recognized labels that are ABOVE threshold into a single csv for ease of moving into sheets, and stops the bot from listening to images.
- **Input:**  
    Example:
    ```
    /ocr-end
    ```
    The bot will send the final collected `ocr_results.csv` and end listening to images. 

---

## How It Works
1. **Inventory Setup:**  
   Use `/add-envelopes` and `/add-stamps` to populate your inventory with envelope types and stamp types.
   
2. **Track Usage:**  
   Record the usage of envelopes and stamps by using the `/estimated-usage` command. The bot will calculate the necessary stamp usage and update the inventory.
   
3. **Group Management:**  
   Use `/list-groups` and `/register` to manage which groups the bot interacts with. Only registered groups can execute restricted commands like `/add-envelopes` and `/estimated-usage`.

4. **Monitoring:**  
   Use `/list-registered` to view all registered groups, and monitor changes in the inventory in real-time.

---

## Notes
- The bot will only respond to commands from registered groups for commands like `/add-envelopes`, `/estimated-usage`, etc.
- Ensure correct input formats, such as providing envelope types and quantities, to avoid errors.
- You must register a group before it can use the bot for specific commands. Use `/list-groups` to get the list of groups and `/register` to enable a group.

For any issues or feedback, contact the bot administrator.

Happy Grinding!
