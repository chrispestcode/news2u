# news2u

News2U

News2U is a web application the aggregates news articles and presents them to the user in a friendly format. News2U was built using Vue, NewsAPI, Bootstrap CSS, and local storage in the browser. Vue is used for efficiency, component-resusabilty, and simplicity.

The user has the ability to search for news articles by keyword by entering text into the search field. Once the text has been entered, the user can press the ‘Enter’ key or click the ‘Search’ button to begin the query.

The user has the ability to save articles by clicking the ‘Save’ button on the respective card. Saved articles will appear in the ‘Saved’ tab in the nav bar.

The card components contains the information of a news article. The card is clickable and will redirect the user to the URL. A design decision was made to include a brief description of the article rather than the url for visual purposes.


File Structure:

Majority of the code is written in the `components` folder. It consists of `Base Card`, `ListingsCard`, `NewsCard`, `NewsListingsCard`, and `SavedNewsListingCard` components.

`Base Card` serves as the foundation for the app, containing the header, footer, and `Listings Card` component.

`ListingsCard` component contains the logic for toggling between `NewsListingsCard` and `SavedNewsListingCard` tabs in the navbar. Any data that may be transferred between these two components can be facilitated through `ListingsCard` component.

`NewsListingsCard` component contains the logic for listing each individual article in a grid format. It evokes an API request upon mounting and saves any saved articles to `localStorage` before destruction.  Here is where the `NewsCard` is contained.

`NewsCard` component contains little functionality besides returning any save functionality back to the parent. It is mainly used for displaying the content and redirecting the user to the link.

`SavedNewsListingCard` is nearly identical to `NewsListingsCard` except that it displays only saved articles and has a filter search field. The filter search field is currently not functional, but it serves a purpose for visual consistency.

Local storage is used to store the saved articles. The current storage requirement is minimal, so a lightweight storage was used.

To run the application, download the file. Navigate to the root folder `news2u`. Ensure that npm is installed : `npm install npm@latest -g` and run the command `npm run serve`. If there are missing dependencies for the command, follow the CLI prompt to install them. After the compilation is successful, navigate to `localhost:8080` in the browser and the application will be available.

Mobile devices are also supported.
