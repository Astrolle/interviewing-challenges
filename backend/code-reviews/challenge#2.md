# Challenge #2

## Describe the errors that you see

```typescript
@Controller('auth')
export class AuthController {
  constructor(private authService: AuthService) {}

  @Post('login')
  async login(@Body() body: any) {
    try {
      const user = await this.authService.validateUser(body.email, body.password);
      
      if (!user) {
        throw new Error('Invalid credentials');
      }

      const token = jwt.sign({ id: user.id }, 'my-secret-key');
      
      return { 
        token,
        user: user 
      };
    } catch (error) {
      return { error: error.message };
    }
  }

  @Get('profile/:id')
  async getProfile(@Param('id') id: string) {
    return await this.authService.getUserProfile(id);
  }
}
```
