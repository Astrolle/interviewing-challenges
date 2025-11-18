# Challenge #3

## Describe the errors that you see

```typescript
@Injectable()
export class UserService {
  constructor(
    @InjectRepository(User)
    private userRepository: Repository<User>,
  ) {}

  async createUser(email: string, password: string, role: string) {
    const user = new User();
    user.email = email;
    user.password = password;
    user.role = role;
    
    return await this.userRepository.save(user);
  }

  async getUser(id: string) {
    const user = await this.userRepository.findOne({ where: { id } });
    return user;
  }

  async updateUser(id: string, data: any) {
    await this.userRepository.update(id, data);
    return { message: 'User updated' };
  }
}
```
