### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor가 사용되지 않음

|   |   |
|---|---|
|설명|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 생성자는 이제 사용되지 않으며 사용하는 경우 빌드 경고가 발생합니다.|
|제안 해결 방법|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 생성자가 계속 작동하지만 .NET Framework 4.5 도구를 사용하여 코드를 다시 컴파일할 때 사용되지 않는 빌드 경고를 방지하려면 다음 생성자를 대신 사용해야 합니다<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|범위|부|
|버전|4.5|
|형식|대상 변경|
|영향을 받는 API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

