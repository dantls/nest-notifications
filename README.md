
# Nest Notifications

A simple and customizable notification module for NestJS applications. This module allows you to easily integrate and manage notifications within your NestJS projects.

## Features

- **Customizable Notifications**: Easily configure and customize notifications to suit your application's needs.
- **Multiple Channels**: Supports various notification channels such as email, SMS, and push notifications.
- **Easy Integration**: Seamlessly integrates with your existing NestJS application.
- **Scalable**: Designed to handle notifications at scale, ensuring reliable delivery.

## Installation

To install the module, run the following command:

```bash
npm install nest-notifications
```

## Usage

1. **Import the Module**: Import the `NotificationsModule` into your application module.

```typescript
import { Module } from '@nestjs/common';
import { NotificationsModule } from 'nest-notifications';

@Module({
  imports: [NotificationsModule.forRoot({ /* configuration options */ })],
})
export class AppModule {}
```

2. **Configure Notification Channels**: Configure the notification channels you want to use.

```typescript
import { NotificationsModule, NotificationChannel } from 'nest-notifications';

@Module({
  imports: [
    NotificationsModule.forRoot({
      channels: [
        NotificationChannel.EMAIL,
        NotificationChannel.SMS,
        NotificationChannel.PUSH,
      ],
    }),
  ],
})
export class AppModule {}
```

3. **Send Notifications**: Use the `NotificationsService` to send notifications.

```typescript
import { Injectable } from '@nestjs/common';
import { NotificationsService } from 'nest-notifications';

@Injectable()
export class AppService {
  constructor(private readonly notificationsService: NotificationsService) {}

  async sendNotification() {
    await this.notificationsService.send({
      channel: 'email',
      message: 'Hello, this is a test notification!',
      recipient: 'user@example.com',
    });
  }
}
```

## Configuration Options

- **channels**: An array of notification channels to enable (e.g., `email`, `sms`, `push`).
- **options**: Additional configuration options for each channel.

## Contributing

Contributions are welcome! Please read the [contributing guide](CONTRIBUTING.md) to get started.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

