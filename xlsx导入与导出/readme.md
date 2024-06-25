# XLSX(Vue版本)

## 使用 Vue主要是为了方便对表格数据进行绑定，然后修改或者删除等等操作.本质上还是js库中的方法.

## 导入

    1.const file=e.target.files[0] 获取第一个导入文件
      const reader=new FileReader() 
      reader.readAsArrayBuffer(file) 以数组形式读取导入的文件

    2.  reader.onload=(e)=>{
        const data=new Uint8Array(e.target.result) 字节流（反正我不是很清楚,用来存储数据的吧算是)
        const workbook=XLSX.read(data,{type:'array'})  (从字节中读取数据)
        const firstSheetName=workbook.SheetNames[0] (读取表头)
        const worksheet=workbook.Sheets[firstSheetName] (读取数据)
        const jsonData=XLSX.utils.sheet_to_json(worksheet) (将数据以工作表的形式转为json)
       
      }

    3. this.jsonData.forEach((item)=>{
        let divTable={
          name:item.姓名,
          age:item.年龄,
          gender:item.性别,
          address:item.地址}

        newTable.push(divTable)
      }) //遍历数组，转为object类型

## 导出

    1.将对象分割成数组类型(例如{name:xxx,age:yyy}=>[[name,age],[xxx,yyy]])
    其中第一个数组表示数据头,其他数组均为数据
    2.let worksheet=XLSX.utils.aoa_to_sheet(tableData) =>转为工作表
      let bookNew=XLSX.utils.book_new() =>转为工作簿
      XLSX.utils.book_append_sheet(bookNew,worksheet)
    3.导出下载
      XLSX.writeFile("默认名字")