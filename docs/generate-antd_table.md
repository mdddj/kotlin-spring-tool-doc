---
sidebar_position: 5
---

# 5.生成Antd Form

![img.png](/antd/img_12.png)


# 示例

kotlin 模型
```kotlin

@Entity
@Schema(name = "存储策略")
class Storage {

    @Id
    @GeneratedValue
    @SchemaProperty(name = "主键ID")
    val id: Long? = null

    @SchemaProperty(name = "存储路径")
    val path: String? = null

    @SchemaProperty(name="策略名称")
    val name: String? = null

    @SchemaProperty(name="备注")
    val note: String? = null

    @SchemaProperty(name="创建时间")
    val createDate: Date? = null

    @SchemaProperty(name="存储策略类型")
    val type: String? = null

}
```

生成的代码

```typescript jsx
import { ModalForm } from '@ant-design/pro-components';
import React from 'react';

export interface Storage {
	id?: number,
	path?: string,
	name?: string,
	note?: string,
	createDate?: Date,
	type?: string,
}

type ModelDef = Storage;

interface Props {
  trigger?: React.JSX.Element;
  onSuccess?: () => void;
  initialValue?: ModelDef;
}

const ModelForm: React.FC<Props> = ({
  trigger,
  onSuccess,
  initialValue,
}) => {
  /// ToDo实现保存/修改请求
  const onSubmit = async (values: ModelDef): Promise<boolean> => {
    return true;
  };

  ///提交数据
  const onFinish = async (values: ModelDef): Promise<boolean> => {
    let r = await onSubmit(values);
    if (r) {
      onSuccess?.();
    }
    return r;
  };

  return (
    <>
      <ModalForm<ModelDef>
        initialValues={initialValue}
        trigger={trigger}
        onFinish={onFinish}
      >
      		<ProFormText name={'id'} label={'id'}  />
		<ProFormText name={'path'} label={'path'}  />
		<ProFormText name={'name'} label={'name'}  />
		<ProFormText name={'note'} label={'note'}  />
		<ProFormDatePicker name={'createDate'} label={'createDate'}  />
		<ProFormText name={'type'} label={'type'}  />

      </ModalForm>
    </>
  );
};

```

