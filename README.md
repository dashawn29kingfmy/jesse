
# Jesse  

**Algo-trading used to be 😵‍💫—we made it 🤩.**  

---

## About Jesse  

Jesse is a powerful crypto trading framework designed to make researching, testing, and implementing your **own trading strategies** as easy as possible.  

### 🚀 Why Choose Jesse?  

In short: **it's more accurate, more intuitive, and quicker to get started with compared to other solutions**.  

With Jesse, you don’t need to worry about complicated setups or coding environments—just download and run the `.exe` file, and you’re ready to go.  

Want to learn more about what makes Jesse stand out?  
👉 Check out Jesse's features and why it’s the perfect fit for your trading needs.  

---

## 📚 Getting Started  

Getting started with Jesse is simple:  
1. [**Download the latest release**](../../releases)
2. Run the program by double-clicking the provided `jesse.exe` file.  

The process is designed to be as smooth as possible—no additional setup required!  

---

### Strategy Code Example:  

Here’s an example of a simple moving average crossover strategy written in Jesse:  

```python
class SMACrossover(Strategy):
    @property
    def slow_sma(self):
        return ta.sma(self.candles, 200)

    @property
    def fast_sma(self):
        return ta.sma(self.candles, 50)

    def should_long(self) -> bool:
        return self.fast_sma > self.slow_sma

    def should_short(self) -> bool:
        return self.fast_sma < self.slow_sma

    def should_cancel_entry(self) -> bool:
        return False

    def go_long(self):
        qty = utils.size_to_qty(self.balance, self.price, fee_rate=self.fee_rate)
        self.buy = qty, self.price

    def go_short(self):
        qty = utils.size_to_qty(self.balance, self.price, fee_rate=self.fee_rate)
        self.sell = qty, self.price

    def update_position(self):
        if self.is_long and self.fast_sma < self.slow_sma:
            self.liquidate()
        if self.is_short and self.fast_sma > self.slow_sma:
            self.liquidate()
```
---

## 🙌 How to Contribute  

Thank you for your interest in contributing to Jesse! Here’s how you can help:  
- **Participate in the community** by helping other users in the Discord.  
- **Submit bug reports and feature requests** to improve the framework.  

---

## ⚠️ Disclaimer  

This software is for **educational purposes only**.  
**Use it at your own risk.**  

The authors and contributors assume no responsibility for any financial losses or trading outcomes. **Never risk more money than you can afford to lose.** This software comes **as is** with no guarantees or warranties, and bugs may exist in the code.  
