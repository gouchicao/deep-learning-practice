# REST服务
> 基于Python语言的开发

## 安装依赖包
```bash
pip install flask
pip install flask_restful
```

## 上传图片
```py
import tempfile
import werkzeug

from flask import Flask
from flask_restful import reqparse, abort, Api, Resource


class UploadImage(Resource):
    def post(self):
        parse = reqparse.RequestParser()
        parse.add_argument('file', type=werkzeug.datastructures.FileStorage, location='files')
        args = parse.parse_args()

        img_file = args['file']

        if not img_file:
            return {'no file'}, 417

        with tempfile.NamedTemporaryFile() as f:
            img_data = args['file'].read()
            f.write(img_data)

        return detect_result, 201


if __name__ == '__main__':
    app = Flask(__name__)
    api = Api(app)

    api.add_resource(UploadImage, '/upload_image')

    app.run(host=0.0.0.0, debug=False)
```

## curl测试
```bash
curl -v -X POST -H "Content-Type: multipart/form-data" -F "file=@test.jpg" http://127.0.0.1:5000/upload_image
```

## 参考资料
* [flask-restful](https://github.com/flask-restful/flask-restful)
* [Flask-RESTful User’s Guide](https://flask-restful.readthedocs.io/en/latest/)
* [使用 Python 和 Flask 设计 RESTful API](http://www.pythondoc.com/flask-restful/first.html)
* [使用 Flask-RESTful 设计 RESTful API](http://www.pythondoc.com/flask-restful/second.html)
* [使用 Flask 设计 RESTful 的认证](http://www.pythondoc.com/flask-restful/third.html)
* [Flask-RESTful快速入门](http://www.pythondoc.com/Flask-RESTful/quickstart.html)
* [使用 Flask-RESTful 设计 RESTful API](https://www.jianshu.com/p/81cd461c7e8f)
* [flask報錯No module named 'flask.ext'](https://www.itread01.com/content/1547562072.html)
* [Flask-RESTful Upload Image](https://stackoverflow.com/questions/28982974/flask-restful-upload-image)
* [Question on File Upload in Restful Flask](https://github.com/flask-restful/flask-restful/issues/485)
