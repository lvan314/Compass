# Compass

一款简易的指南针插件，使用简单，只需获取传感器倾斜角传给View即可。

## 效果图

AS上引用截图

![效果图](https://github.com/lvan314/Compass/blob/master/compassview.png)

### 引用方式

```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
  ```
  
  ```
  dependencies {
	        implementation 'com.github.Lvan314:Compass:Tag'
	}
  ```

### 使用
参数定义
```
    private SensorManager sensorManager;
    private SensorEventListener sensorEventListener;
    private CompassView compassView;
    private  float val;
```
获取角度以及传值
```
sensorManager = (SensorManager) getSystemService(SENSOR_SERVICE);
        compassView=findViewById(R.id.compass);
        sensorEventListener = new SensorEventListener() {
            @Override
            public void onSensorChanged(SensorEvent event) {
                val = event.values[0];
                compassView.setVal(val);
            }
            @Override
            public void onAccuracyChanged(Sensor sensor, int accuracy) {
            }
        };
        sensorManager.registerListener(sensorEventListener,sensorManager.getDefaultSensor(Sensor.TYPE_ORIENTATION),
                SensorManager.SENSOR_DELAY_GAME);
```
    
