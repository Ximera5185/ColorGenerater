# ColorGenerater
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ColorGenerater
{
    private List<Color> _colors = new ()
        {
            Color.black,
            Color.blue,
            Color.green,
            Color.red,
            Color.yellow,
            Color.cyan
        };
        
    public Color GetRandomColor()
    {
        return _colors [Random.Range(0, _colors.Count)];
    }
}
Клас без наследования от MonoBehaviour (позволяет не использовать объект на сцене, а из кода обращаться к скрипту)
public class Cube : MonoBehaviour
{
    private Renderer _renderer;

    private void Start()
    {
        _renderer = GetComponent<Renderer>(); получаем ссылку у куба на цвет
    }

    public void SetColor(Color color)  вызавем метод у экземпляра куба для установки цвета и передадим в него сгенерированный цвет классом ColorGenerater
    {
        _renderer.material.color = color;
    }
}
Также варианты назначения цвета с применением этого класса -- newCube.SetColor(_colorGenerater.GetRandomColor()); --

Также варианты без использования данного класса : 
1 - newCube.GetComponent<Renderer>().material.color = Random.ColorHSV();  -- Random.ColorHSV(); Рандомно генирирует не предсказуемый цвет--
