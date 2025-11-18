# Challenge #2

## Identify what errors do you see

```JSX
function ShoppingCart() {
  const [cart, setCart] = useState([]);
  const [total, setTotal] = useState(0);
  const [itemCount, setItemCount] = useState(0);

  const addToCart = (product) => {
    cart.push(product);
    setCart(cart);
    setTotal(total + product.price);
    setItemCount(itemCount + 1);
  };

  const removeFromCart = (productId) => {
    const product = cart.find(p => p.id === productId);
    const index = cart.indexOf(product);
    cart.splice(index, 1);
    setCart(cart);
    setTotal(total - product.price);
    setItemCount(itemCount - 1);
  };

  const updateQuantity = (productId, quantity) => {
    const product = cart.find(p => p.id === productId);
    const oldQuantity = product.quantity;
    product.quantity = quantity;
    setCart(cart);
    setTotal(total + (product.price * (quantity - oldQuantity)));
  };

  return (
    <div>
      <div>Items: {itemCount}</div>
      <div>Total: ${total}</div>
      {cart.map(item => (
        <CartItem 
          key={item.id} 
          item={item}
          onRemove={removeFromCart}
          onUpdate={updateQuantity}
        />
      ))}
    </div>
  );
}
```
