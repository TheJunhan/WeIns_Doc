# Week4

## 07-27

### Emoji

> v-emoji-picker@2.3.0

```javascript
import VEmojiPicker from 'v-emoji-picker'
<VEmojiPicker
      v-show="showDialog"
      labelSearch="Search"
      lang="pt-BR"
      @select="onSelectEmoji"
    />

onSelectEmoji(emoji) {
    this.text += emoji.data;
}
```

- [Demo](https://codesandbox.io/s/vue-example-emoji-picker-2-746pq?file=/src/components/Demo.vue)

- [github](https://github.com/joaoeudes7/V-Emoji-Picker)

- 在评论时使用表情，由于comment数据库为mysql，会出现不支持的情况，只需要将该表的字符集设置成utf8mb4

> alter table comment convert to character set utf8mb4 collate utf8mb4_bin;

## 07-28

## 07-29

## 07-30

## 07-31
