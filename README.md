# **Spotify Re-Wrapped: Project by Ezra Gershman**

## **Description**
Spotify Wrapped for 2024 didn’t quite hit the mark, so I decided to take matters into my own hands. This project dives into my actual listening data to get a better picture of my music tastes. By analyzing various aspects of my Spotify history, I can uncover patterns, preferences, and trends that Spotify's summary might have missed. From listening times and favorite artists to genre distributions, this project aims to create a more accurate and personalized Spotify Re-Wrapped experience.

## **Installation**

To get started with the Spotify Re-Wrapped project, follow these steps:

1. **Clone the repository:**
    ```bash
    git clone https://github.com/ezragershman/spotify-listening-data.git
    ```

2. **Navigate to the project directory:**
    ```bash
    cd spotify-listening-data
    ```

3. **Set up a virtual environment (optional but recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

4. **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

5. **Set up your environment variables:**
    - Create a `.env` file in the project root directory.
    - Add your Spotify API credentials and any other necessary environment variables to the `.env` file.

6. **Run the project:**
    - Follow the instructions in the **Usage** section to start using the functions and analyzing your data.





## **Formulas & Algorithms**

### **Generic Diversity Growth Formula**

The formula for calculating the diversity growth percentage for any category is:

$$
\text{Growth Percentage} = \left( \frac{\text{Current Count} - \text{Previous Count}}{\text{Previous Count}} \right) \times 100
$$

Where:
- **Current Count**: The number of unique elements (e.g., genres, artists, etc.) in the current time period.
- **Previous Count**: The number of unique elements in the previous time period.

### **Weighted Listening Time for Multiple Artists**

For a track involving multiple artists, we calculate the weighted listening time as follows:

1. **Listen Value as a Decimal**:
   - Each listen is valued as a decimal/percentage between 0 and 1 based on the proportion of the track listened to.

2. **Check Unique Artists**:
   - Identify the unique values in both the `artistName` and `artists_involved` columns.

3. **Division of Weighted Listen Value**:
   - Half of the listen value is awarded to the main artist (`artistName`).
   - The remaining half of the listen value is divided equally among the other contributing artists in `artists_involved`.

#### **Mathematical Formula**

Given:
- \( L \) is the listen value as a percentage (between 0 and 1).
- \( A \) is the main artist (from `artistName`).
- \( C \) is the number of contributing artists (excluding the main artist).

The listen value awarded to the main artist \( A \) is:

$$
\text{Listen Value}_{A} = \frac{L}{2}
$$

The listen value awarded to each contributing artist \( C_i \) in `artists_involved` is:

$$
\text{Listen Value}_{C_i} = \frac{L}{2 \times (N - 1)}
$$

where \( N \) is the total number of unique artists (including the main artist).

#### **Example**

If the listen value \( L \) is 0.8 and there are 4 unique artists (including the main artist):

- Main artist listen value: $$ \frac{0.8}{2} = 0.4 $$
- Contributing artist listen value: $$ \frac{0.8}{2 \times (4 - 1)} = \frac{0.8}{6} \approx 0.1333 $$
for each of the 3 contributing artists.

This ensures that the main artist receives a significant portion of the listen value, while the remaining value is fairly distributed among the contributing artists.

