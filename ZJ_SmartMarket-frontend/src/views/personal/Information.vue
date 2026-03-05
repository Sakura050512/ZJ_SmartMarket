<style scoped>
.information-container {
  padding: 20px;
  background-color: #f5f7fa;
  min-height: 100vh;
}

/* 面包屑样式 */
.custom-breadcrumb {
  margin-bottom: 20px;
  font-size: 14px;
}

/* 页面标题 */
.page-title {
  margin-bottom: 25px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.page-title i {
  font-size: 32px;
  color: #409EFF;
}
.page-title span {
  font-size: 24px;
  font-weight: 600;
  color: #303133;
  letter-spacing: 1px;
}

/* 卡片样式 */
.profile-card {
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.05);
  transition: box-shadow 0.3s;
}
.profile-card:hover {
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.1);
}

.profile-form {
  padding: 10px 20px 20px;
}

/* 头像上传区域 */
.avatar-wrapper {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}
.avatar-uploader {
  border: 1px dashed #d9d9d9;
  border-radius: 50%;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: border-color 0.3s;
  width: 120px;
  height: 120px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.avatar-uploader:hover {
  border-color: #409EFF;
}
.avatar-uploader-icon {
  font-size: 28px;
  color: #8c939d;
  width: 120px;
  height: 120px;
  line-height: 120px;
  text-align: center;
  background-color: #fbfdff;
}
.avatar {
  width: 120px;
  height: 120px;
  display: block;
  object-fit: cover;
  border-radius: 50%;
}

/* 表单项统一样式 */
.el-form-item {
  margin-bottom: 22px;
}
.el-form-item__label {
  font-weight: 500;
  color: #606266;
}
.el-input__inner,
.el-textarea__inner,
.el-select .el-input__inner {
  border-radius: 8px;
  transition: all 0.2s;
}
.el-input__inner:hover,
.el-textarea__inner:hover {
  border-color: #b3d8ff;
}
.el-input__inner:focus,
.el-textarea__inner:focus {
  border-color: #409EFF;
  box-shadow: 0 0 0 2px rgba(64, 158, 255, 0.1);
}

/* 下拉框宽度自适应 */
.full-width-select {
  width: 100%;
}

/* 缩短输入框宽度 */
.profile-form .el-input,
.profile-form .el-select,
.profile-form .el-textarea {
  width: 90%;
  min-width: 200px;
}

.profile-form .el-form-item__content {
  display: flex;
  justify-content: flex-start;
}

/* 按钮区域 */
.form-actions {
  margin-top: 30px;
  gap: 20px;
}
.el-button {
  border-radius: 20px;
  padding: 12px 30px;
  font-size: 16px;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  gap: 5px;
}
.el-button i {
  font-size: 18px;
}

/* 修改主按钮为纯淡蓝色 */
.el-button--primary {
  background: #79bbff;  /* 淡蓝色，可根据喜好调整 */
  border: none;
}
.el-button--primary:hover {
  background: #a0cfff;  /* 悬停时稍深一点的淡蓝 */
  box-shadow: 0 4px 12px rgba(121, 187, 255, 0.4);
}
.el-button--default {
  border: 1px solid #dcdfe6;
  background-color: #fff;
}
.el-button--default:hover {
  background-color: #f5f7fa;
  border-color: #c0c4cc;
}
</style>