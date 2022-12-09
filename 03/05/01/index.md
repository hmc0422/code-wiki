---

### 基础正则表达式速查表

<!-- tabs:start -->

#### **字符**

<table>
  <tr>
    <td><strong>表达式</strong></td>
    <td><strong>描述</strong></td>
  </tr>
  <tr>
    <td><code>[abc]</code></td>
    <td>字符集。匹配集合中所含的任一字符。</td>
  </tr>
  <tr>
    <td><code>[^abc]</code></td>
    <td>否定字符集。匹配任何不在集合中的字符。</td>
  </tr>
  <tr>
    <td><code>[a-z]</code></td>
    <td>字符范围。匹配指定范围内的任意字符。</td>
  </tr>
  <tr>
    <td><code>.</code></td>
    <td>匹配除换行符以外的任何单个字符。</td>
  </tr>
  <tr>
    <td><code>\</code></td>
    <td>转义字符。</td>
  </tr>
  <tr>
    <td><code>\w</code></td>
    <td>匹配任何字母数字，包括下划线（等价于<code>[A-Za-z0-9_]</code>）。</td>
  </tr>
  <tr>
    <td><code>\W</code></td>
    <td>匹配任何非字母数字（等价于<code>[^A-Za-z0-9_]</code>）。</td>
  </tr>
  <tr>
    <td><code>\d</code></td>
    <td>数字。匹配任何数字。</td>
  </tr>
  <tr>
    <td><code>\D</code></td>
    <td>非数字。匹配任何非数字字符。</td>
  </tr>
  <tr>
    <td><code>\s</code></td>
    <td>空白。匹配任何空白字符，包括空格、制表符等。</td>
  </tr>
  <tr>
    <td><code>\S</code></td>
    <td>非空白。匹配任何非空白字符。</td>
  </tr>
</table>

#### **分组和引用**

<table>
  <tr>
    <td><strong>表达式</strong></td>
    <td><strong>描述</strong></td>
  </tr>
  <tr>
    <td><code>(expression)</code></td>
    <td>分组。匹配括号里的整个表达式。</td>
  </tr>
  <tr>
    <td><code>(?:expression)</code></td>
    <td>非捕获分组。匹配括号里的整个字符串但不获取匹配结果，拿不到分组引用。</td>
  </tr>
  <tr>
    <td><code>\num</code></td>
    <td>对前面所匹配分组的引用。比如<code>(\d)\1</code>可以匹配两个相同的数字，<code>(Code)(Sheep)\1\2</code>则可以匹配<code>CodeSheepCodeSheep</code>。</td>
  </tr>
</table>


#### **锚点/边界**

<table>
  <tr>
    <td><strong>表达式</strong></td>
    <td><strong>描述</strong></td>
  </tr>
  <tr>
    <td><code>^</code></td>
    <td>匹配字符串或行开头。</td>
  </tr>
  <tr>
    <td><code>$</code></td>
    <td>匹配字符串或行结尾。</td>
  </tr>
  <tr>
    <td><code>\b</code></td>
    <td>匹配单词边界。比如<code>Sheep\b</code>可以匹配<code>CodeSheep</code>末尾的<code>Sheep</code>，不能匹配<code>CodeSheepCode</code>中的<code>Sheep</code></td>
  </tr>
  <tr>
    <td><code>\B</code></td>
    <td>匹配非单词边界。比如<code>Code\B</code>可以匹配<code>HelloCodeSheep</code>中的<code>Code</code>，不能匹配<code>HelloCode</code>中的<code>Code</code>。</td>
  </tr>
</table>

#### **数量表示**

<table>
  <tr>
    <td><strong>表达式</strong></td>
    <td><strong>描述</strong></td>
  </tr>
  <tr>
    <td><code>?</code></td>
    <td>匹配前面的表达式0个或1个。即表示可选项。</td>
  </tr>
  <tr>
    <td><code>+</code></td>
    <td>匹配前面的表达式至少1个。</td>
  </tr>
  <tr>
    <td><code>*</code></td>
    <td>匹配前面的表达式0个或多个。</td>
  </tr>
  <tr>
    <td><code>|</code></td>
    <td>或运算符。并集，可以匹配符号前后的表达式。</td>
  </tr>
  <tr>
    <td><code>{m}</code></td>
    <td>匹配前面的表达式m个。</td>
  </tr>
  <tr>
    <td><code>{m,}</code></td>
    <td>匹配前面的表达式最少m个。</td>
  </tr>
  <tr>
    <td><code>{m,n}</code></td>
    <td>匹配前面的表达式最少m个，最多n个。</td>
  </tr>
</table>

#### **预查断言**

<table>
  <tr>
    <td><strong>表达式</strong></td>
    <td><strong>描述</strong></td>
  </tr>
  <tr>
    <td><code>(?=)</code></td>
    <td>正向预查。比如<code>Code(?=Sheep)</code>能匹配<code>CodeSheep</code>中的<code>Code</code>，但不能匹配<code>CodePig</code>中的<code>Code</code>。</td>
  </tr>
  <tr>
    <td><code>(?!)</code></td>
    <td>正向否定预查。比如<code>Code(?!Sheep)</code>不能匹配<code>CodeSheep</code>中的<code>Code</code>，但能匹配<code>CodePig</code>中的<code>Code</code>。</td>
  </tr>
  <tr>
    <td><code>(?<=)</code></td>
    <td>反向预查。比如<code>(?<=Code)Sheep</code>能匹配<code>CodeSheep</code>中的<code>Sheep</code>，但不能匹配<code>ReadSheep</code>中的<code>Sheep</code>。</td>
  </tr>
  <tr>
    <td><code>(?&lt!)</code></td>
    <td>反向否定预查。比如<code>(?&lt!Code)Sheep</code>不能匹配<code>CodeSheep</code>中的<code>Sheep</code>，但能匹配<code>ReadSheep</code>中的<code>Sheep</code>。</td>
  </tr>
</table>

#### **特殊标志**

<table>
  <tr>
    <td><strong>表达式</strong></td>
    <td><strong>描述</strong></td>
  </tr>
  <tr>
    <td><code>/.../i</code></td>
    <td>忽略大小写。</td>
  </tr>
  <tr>
    <td><code>/.../g</code></td>
    <td>全局匹配。</td>
  </tr>
  <tr>
    <td><code>/.../m</code></td>
    <td>多行修饰符。用于多行匹配。</td>
  </tr>
</table>

<!-- tabs:end -->
