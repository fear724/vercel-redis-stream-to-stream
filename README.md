# Express.js on Vercel

Basic Express.js + Vercel example that serves html content, JSON data and simulates an api route. 
Includes Redis stream reading and a serverless consumer that runs on Vercel cron.

## Features

- Express.js web server
- Redis stream reading API endpoint
- Serverless Redis stream consumer (runs every 1 hour via Vercel cron)
- TypeScript support

## How to Use

You can choose from one of the following two methods to use this repository:

### One-Click Deploy

Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=vercel-examples):

### Clone and Deploy

```bash
git clone [repository ...]
```

Install the dependencies:

```bash
pnpm install
```

```bash
pnpm build
```

Install the Vercel CLI:

```bash
npm i -g vercel
```

Then run the app at the root of the repository:

```bash
vercel dev
```

## Redis Setup

Create `.env` file with configuration

The app includes Redis stream functionality. Set the following environment variables:

- `REDIS_URL`: Redis connection URL (default: `redis://localhost:6379`)
- `REDIS_STREAM_NAME`: Name of the Redis stream (default: `mystream`)
- `REDIS_GROUP_NAME`: Consumer group name (default: `mygroup`)
- `REDIS_CONSUMER_NAME`: Consumer name (default: `vercel-consumer`)

## API Endpoints

- `/healthz`: Health check
- `/api/consumer`: Manual trigger for the consumer (GET) for crone job

## Consumer

The Redis stream consumer runs automatically every 1 hour via Vercel cron. 
It processes pending messages in the consumer group and acknowledges them.

You can also manually trigger the consumer by visiting `/api/consumer`.
