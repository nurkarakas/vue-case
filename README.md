#  Vue Case

✨ Powered by Modern Technologies

- Vue 3: A powerful framework for building interactive and dynamic user interfaces with ease.
- Tailwind: A utility-first CSS framework designed for rapid and flexible UI development.
- Pinia: A simple and intuitive state management solution for Vue 3 applications.
- Vite: A fast and efficient build tool that optimizes the development experience.


## Demo


## Credentials

- homework@eva.guru
- Homeworkeva1**

## Component Structure

- **Skeletons**

  - ChartSkeleton: A loading placeholder for displaying charts.
  - TableSkeleton: A loading placeholder for table data.

- Chart: The component responsible for rendering the charts.

- GetErrorSuccess: Handles and displays error or success messages.
- VueTable: A component that provides table functionality with pagination and search features.

## Layout Structure

The repository comes with a well-organized layout structure that can be easily implemented. To add a new layout, just define its name in the router while setting up a new route. All layout management is handled within the loadLayoutMiddleware.js file.

## View Structure

This repository contains two primary views:

- Home (Login Screen): The initial screen where users can log in.
- Dashboard: Shows charts and associated tables for data visualization.


## CONSTANTS!

The `CONSTANTS.js` file defines crucial constants for the application:

```javascript
// CONSTANTS.js
export default {
  api: {
    login: 'oauth/token',
    me: 'user/user-information',
    sales: {
      dailySalesOverview: 'data/daily-sales-overview',
      skuData: 'data/daily-sales-sku-list',
      skuRefundRates: 'data/get-sku-refund-rate',
    },
  },
  dailySalesOverviewDays: [7, 14, 30, 60],
  defaultCurrency: '$',
  defaultRecordPerPage: 10,
  defaultRecordSize: 30,
  errors: {
    dashboard: { maxComparisonDays: 'You can not compare more than 2 days' },
    noData: 'No data available',
    sales: { errorFetching: 'Error fetching sales' },
    users: { loginError: 'Invalid Credentials', invalidToken: 'Invalid Token' },
  },
  maxComparisonDays: 2,
  routes: { dashboard: '/dashboard' },
}
```

## .env

```
VITE_OPENAI_API_BASEURL=https://iapitest.eva.guru/
```

## 🚀 Features

**State Management**

- **Pinia**: Simplified and intuitive state management for maintaining the application state.

**Efficient Development Workflow**

- **Vite**: Fast build tool for an efficient development experience.
- **Modular Code Structure**: Clean and maintainable codebase with Vue 3's Composition API.




