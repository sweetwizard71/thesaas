# AI Model Interaction Platform with Replicate API

A dynamic Next.js platform that integrates with Replicate API to manage AI chat and image generation models, featuring an admin panel for configuration, local storage for history management, and monetization through ads.

## Features

- **Admin Panel** - Manage API keys, add/remove models, and configure ad placements without code changes
- **Chat Interface** - Intuitive chat UI with message history, model switching capabilities, and localStorage persistence
- **Image Generation** - Prompt-based image generator with gallery view and download options
- **API Integration** - Replicate API connection with dynamic model switching for both chat and image generation
- **Monetization** - Ad placements for free users with options for subscription-based premium features
- **Custom Code Injection** - Add custom header and footer code across all pages

## Prerequisites

- Node.js 18.x or higher
- Supabase account
- Replicate API account
- Git

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <repository-url>
cd <repository-name>
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Set Up Supabase

1. Create a new Supabase project at [https://supabase.com](https://supabase.com)
2. Get your Supabase URL and anon key from the project settings
3. Run the initial migrations to set up the database schema:
   - Navigate to the SQL editor in your Supabase dashboard
   - Copy and paste the contents of `supabase/migrations/initial-setup.sql` and execute it
   - Run each migration file in the `supabase/migrations` folder in numerical order

### 4. Set Up Environment Variables

Create a `.env.local` file in the root directory with the following variables:

```
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_KEY=your_supabase_service_key
SUPABASE_PROJECT_ID=your_supabase_project_id
REPLICATE_API_KEY=your_replicate_api_key
```

### 5. Create an Admin User

1. Sign up for a new account through the application's sign-up page
2. In your Supabase dashboard, go to the SQL editor and run the following query, replacing the email with your account's email:

```sql
UPDATE public.users
SET is_admin = true
WHERE id = (SELECT id FROM auth.users WHERE email = 'your-email@example.com');
```

3. Sign out and sign back in to apply the admin role changes

### 6. Run the Development Server

```bash
npm run dev
```

Visit `http://localhost:3000` to see the application.

## Deployment

### Deploying to Vercel

1. Push your code to a GitHub repository
2. Create a new project on [Vercel](https://vercel.com)
3. Connect your GitHub repository
4. Add all the environment variables from your `.env.local` file to the Vercel project settings
5. Deploy the project

### Deploying to Other Platforms

For other platforms like Netlify, Railway, or a custom server:

1. Build the project:

```bash
npm run build
```

2. Start the production server:

```bash
npm start
```

## Admin Panel Configuration

After logging in as an admin user, navigate to `/dashboard/admin` to access the admin panel. Here you can:

### Manage AI Models

1. Add new AI models for chat or image generation
2. Configure model parameters
3. Enable/disable models

### Configure Ad Placements

1. Navigate to the "Ads" tab in the admin panel
2. Add ad blocks to different pages
3. Configure ad content and placement
4. Enable/disable specific ad placements

### Add Custom Website Code

1. Navigate to the "Website Code" tab in the admin panel
2. Add custom header code that will be injected into the `<head>` of all pages
3. Add custom footer code that will be injected before the closing `</body>` tag
4. Click "Save Changes" to apply the custom code

## User Guide

### Chat Interface

- Navigate to `/dashboard/chat`
- Select a chat model from the dropdown
- Type your message and send
- Chat history is saved in localStorage

### Image Generation

- Navigate to `/dashboard/images`
- Select an image model from the dropdown
- Enter a prompt and generate images
- Download generated images or view your gallery

## Troubleshooting

### Database Issues

If you encounter database-related errors:

1. Check that all migrations have been applied correctly
2. Verify your Supabase credentials in the environment variables
3. Ensure your Supabase service is running

### API Connection Issues

If the Replicate API is not working:

1. Verify your Replicate API key in the environment variables
2. Check the model IDs in the admin panel match those on Replicate
3. Ensure you have sufficient credits in your Replicate account

### Custom Code Injection Issues

If your custom header or footer code is not working:

1. Check the browser console for any JavaScript errors
2. Verify that the code is properly formatted
3. Make sure you've clicked "Save Changes" after adding the code
4. Refresh the page to see the changes

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a pull request

## License

[MIT](LICENSE)
