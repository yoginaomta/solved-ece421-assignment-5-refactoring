Download Link: https://assignmentchef.com/product/solved-ece421-assignment-5-refactoring
<br>
<strong>Question 1:</strong> Consider the following code:

<table width="634">

 <tbody>

  <tr>

   <td width="50">  }         </td>

   <td width="384">pub struct L{x: usize,y: usize,pub fn foo (text: &amp;str, string: &amp;str)-&gt;Vec&lt;L&gt; let mut r= Vec::new(); let mut x=0;for line in text.lines(){for (y, _) in line.match_indices(string){r.push(L{x : x,            y: y,})</td>

   <td width="200">{</td>

  </tr>

  <tr>

   <td width="50">    }</td>

   <td width="384">} x+=1; } r</td>

   <td width="200"> </td>

  </tr>

 </tbody>

</table>

a- What does this program do?  b- Try running the <em>Foo </em>function with the following code and report the output.

<table width="639">

 <tbody>

  <tr>

   <td width="639">let results = foo(“Shall I compare thee to a summer’s day?Thou art more lovely and more temperate:Rough winds do shake the darling buds of May, And summer’s lease hath all too short a date:Sometimes too hot the eye of heaven shines, And too often is his gold complexion dimm’d:And every fair from fair sometimes declines,By chance or natures changing course untrimm’d;By thy eternal summer shall not fade,Nor lose possession of that fair thou owest;Nor shall Death brag thou wander’st in his shade,When in eternal lines to time thou growest:So long as men can breathe or eyes can see,So long lives this and this gives life to thee.”, “the”); for x in results {println!(“x : {}, y : {}”, x.x, x.y);}</td>

  </tr>

 </tbody>

</table>

<strong>Question 2:</strong> Convert the <em>foo</em> function to the functional style by applying the following refactorings:

a- Apply iterators to replace the need to manually track y at line 9. b- Use the map function to replace the need to manually update the <em>r</em> vectors.

c- Keep adding iterators until the for loops and let statements (in function foo) disappear.

<strong>Question 3: Consider the following code: </strong>

<table width="639">

 <tbody>

  <tr>

   <td width="639">use std::collections::HashMap; #[derive(Debug)] struct TrieNode {chs: HashMap&lt;char, TrieNode&gt;,     value: Option&lt;i32&gt;,} #[derive(Debug)] struct Trie {     root: TrieNode,}impl Trie {fn new() -&gt; Trie {         Trie {root: TrieNode {                 chs: HashMap::new(),                 value: None,},}}fn add_string(&amp;mut self, string: String, value: i32) {         let mut current_node = &amp;mut self.root;         for c in string.chars() {current_node = current_node.chs.entry(c).or_insert(TrieNode {                     chs: HashMap::new(),                     value: None,});}current_node.value = Some(value);}}fn main() {let mut trie = Trie::new();     trie.add_string(“B”.to_string(), 1);     trie.add_string(“Bar”.to_string(), 2);     println!(“{:#?}”, trie);}</td>

  </tr>

 </tbody>

</table>

The above code implements a Trie (<a href="https://docs.rs/radix_trie/0.0.9/radix_trie/struct.Trie.html#method.len">https://docs.rs/radix_trie/0.0.9/radix_trie/struct.Trie.html#method.len</a><a href="https://docs.rs/radix_trie/0.0.9/radix_trie/struct.Trie.html#method.len">)</a> which is a data-structure for storing and querying string-like keys and associated values.

<ul>

 <li>Add your own implementation for <em>length(&amp;self)-&gt;usize</em> that returns the number of elements stored in the trie.</li>

 <li>Add your own implementation for <em>iter(&amp;self) </em>which returns an iterator over the keys and values of the Trie.</li>

 <li>Add your own implementation for <em>find(&amp;self, key: &amp;String) -&gt; Option&lt;&amp;TrieNode&gt; </em>which searches the Trie for a given key and returns a reference to that key’s corresponding node if found.</li>

 <li>Add your own implementation for <em>delete(&amp;mut self, key: &amp;String) -&gt; Option&lt;i32&gt;</em> to remove a key (from a Trie) and returns the value corresponding to that key.</li>

</ul>