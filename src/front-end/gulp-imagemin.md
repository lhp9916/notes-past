# gulp 压缩图片

### 安装
```
npm init -y
npm install --save-dev gulp gulp-imagemin
```
### add gulpfile.js

```javascript
const gulp = require('gulp');
const imagemin = require('gulp-imagemin');

gulp.task('compress', () =>
    gulp.src('src/images/*/*')
        .pipe(imagemin())
        .pipe(gulp.dest('dist/images'))
);
```
### 压缩
```
gulp compress
```
