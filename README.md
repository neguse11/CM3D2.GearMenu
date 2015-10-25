# CM3D2の歯車メニュー操作

画面右上にある歯車メニューを操作するライブラリです。以下の機能があります

 - 歯車メニューへのアイコンの登録、削除
 - 登録したアイコンの押下時の通知


## サンプル

下記のコードは以下の動作を行うサンプルです

 - 歯車メニューへのアイコン登録
 - アイコンの押下による[Behaviour.enabled](http://docs.unity3d.com/ScriptReference/Behaviour-enabled.html)の変更
 - Behaviour.enabledの変更時にアイコンの枠の色を変更

```C#
namespace CM3D2.Example.Plugin
{
    [PluginName("Example"), PluginVersion("0.0.0.1")]
    public class ExamplePlugin : UnityInjector.PluginBase
    {
        GameObject goButton;
        void Awake() {
            goButton = GearMenu.Buttons.Add(this, null, (go) => { enabled = !enabled; });
        }
        void OnEnable() {
            GearMenu.Buttons.SetFrameColor(goButton, Color.red);
        }
        void OnDisable() {
            GearMenu.Buttons.ResetFrameColor(goButton);
        }
        void OnGUI() {
            GUI.Label(new Rect(0, 0, Screen.width, Screen.height), Name);
        }
    }
}
```


## コードの起源

CM3D2-01さんの「[CM3D2：SystemShortcutにボタン追加](https://gist.github.com/CM3D2-01/adcf5072ff5ba812858a)」を基に改変しています


## ライセンス

 - 調整中です
