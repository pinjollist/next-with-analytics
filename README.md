# next-with-analytics

> Minimalistic analytics helper for Next.js which respects Do Not Track (DNT) headers.

`next-with-analytics` is a tiny HOC that wraps a Next.js application with `react-ga` and some useful analytics helpers. It also allows you to respect Do Not Track (DNT) settings for visitors that have them enabled.

## Installation

```bash
# yarn
yarn add @pinjollist/next-with-analytics

# npm
npm install --save @pinjollist/next-with-analytics
```

## Usage

To use it, wrap your `_app` page with the HOC, passing the `next/router` instance, and some preferred options.

```jsx
// pages/app.js

// ...

const options = {
  trackingCode: process.env.GOOGLE_ANALYTICS,
  respectDNT: true,
};
const nextWithAnalytics = withAnalytics(Router, options);
```

### Options

#### `trackingCode?: string`

The Google Analytics tracking code of your website. Default: `''`

#### `respectDNT?: boolean`

Set to `true` to make the module respect Do Not Track (DNT). This will prevent `react-ga` to be initialised if your browser has DNT enabled. Default: `false`

## Using Analytics helpers

This HOC injects several analytics helper functions into your page. You can access it from `this.props.analytics`. Typings for TypeScript projects are also available as `WithAnalyticsProps`.

```jsx
import Link from 'next/link';

function IndexPage({ analytics }) {
  const handleClick = () => {
    if (analytics.event) {
      analytics.event('Button Click', 'Signup to Platform');
    }
  };

  return (
    <Layout>
      <Container>
        <h1>Try out our platform!</h1>
        <Link href="/signup" onClick={handleClick}>
          <a>Signup Now</a>
        </Link>
      </Container>
    </Layout>
  );
}
```

### List of Helpers

[TODO]
