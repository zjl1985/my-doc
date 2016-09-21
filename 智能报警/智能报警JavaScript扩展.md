#### pom引用
```xml
        <dependency>
            <groupId>com.gaoxin</groupId>
            <artifactId>intelligent-alarm-plugin</artifactId>
            <version>${project.release.version}</version>
        </dependency>
```

#### js引用
```jsp
<script src="<%= request.getContextPath()%>/assets/global/scripts/intelligent-alarm-plugin.js" type="text/javascript"></script>
```

#### js使用
```javascript
IntelligentAlarmPlugin.initIntAlarm(indexId,indexName);
```

> indexId:指标id
> indexName:指标名称 可以为null