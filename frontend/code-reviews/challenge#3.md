# Challenge #3

## Identify what errors do you see

```JSX
function RegistrationForm() {
  const [formData, setFormData] = useState({
    email: '',
    password: '',
    confirmPassword: ''
  });
  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    setFormData({
      [e.target.name]: e.target.value
    });
  };

  const validate = () => {
    const newErrors = {};

    if (!formData.email.includes('@')) {
      newErrors.email = 'Invalid email';
    }
    
    if (formData.password.length < 8) {
      newErrors.password = 'Password too short';
    }
    
    if (formData.password !== formData.confirmPassword) {
      newErrors.confirmPassword = 'Passwords do not match';
    }
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleSubmit = async (e) => {
    e.preventDefault();

    if (validate()) {
      const response = await fetch('/api/register', {
        method: 'POST',
        body: JSON.stringify(formData)
      });
      
      alert('Registration successful!');
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input name="email" value={formData.email} onChange={handleChange} />
      {errors.email && <span>{errors.email}</span>}

      <input name="password" value={formData.password} onChange={handleChange} />
      {errors.password && <span>{errors.password}</span>}
      
      <input name="confirmPassword" value={formData.confirmPassword} onChange={handleChange} />
      {errors.confirmPassword && <span>{errors.confirmPassword}</span>}
      
      <button type="submit">Register</button>
    </form>
  );
}
```
