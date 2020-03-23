---
title: Korzystanie z zasobów 3D w grze lub aplikacji
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d38f87970d5f9ff6d90befc61073cc4ed3d4ca92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589828"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Jak: Korzystanie z zasobów 3D w grze lub aplikacji

W tym artykule opisano, jak można używać programu Visual Studio do przetwarzania zasobów 3D i dołączania ich do kompilacji.

Po użyciu narzędzi w programie Visual Studio do tworzenia zasobów 3D następnym krokiem jest użycie ich w aplikacji. Ale zanim będzie można z nich korzystać, zasoby muszą zostać przekształcone w formacie, który directx może zrozumieć. Aby ułatwić przekształcanie zasobów, visual studio zapewnia dostosowania kompilacji dla każdego rodzaju zasobu, który może produkować. Aby uwzględnić zasoby w kompilacji, wszystko, co musisz zrobić, to skonfigurować projekt, aby użyć dostosowań kompilacji, dodać zasoby do projektu i skonfigurować zasoby, aby użyć poprawnego dostosowywania kompilacji. Następnie możesz załadować zasoby do aplikacji i używać ich, tworząc i wypełniając zasoby DirectX, tak jak w każdej innej aplikacji DirectX.

## <a name="configure-your-project"></a>Konfigurowanie projektu

Przed wdrożeniem zasobów 3D w ramach kompilacji program Visual Studio musi wiedzieć o rodzajach zasobów, które chcesz wdrożyć. Visual Studio już wie o wielu typowych typów plików, ale ponieważ tylko niektóre rodzaje aplikacji używać zasobów 3D, Visual Studio nie zakłada, że projekt będzie tworzyć tego rodzaju plików. Program Visual Studio informuje, że aplikacja używa tego rodzaju zasobów przy użyciu *dostosowań kompilacji*— plików, które informują program Visual Studio, jak przetwarzać różne typy plików w użyteczny sposób — które są dostarczane dla każdego typu zasobu. Ponieważ te dostosowania są stosowane na podstawie projektu, wszystko, co musisz zrobić, to dodać odpowiednie dostosowania do projektu.

### <a name="to-add-the-build-customizations-to-your-project"></a>Aby dodać dostosowania kompilacji do projektu

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Konsuj dostosowania kompilacji** > **build.**

   Zostanie wyświetlone okno dialogowe **Pliki dostosowań kompilacji języka Visual C++.**

2. W obszarze **Dostępne pliki dostosowywania kompilacji**zaznacz pola wyboru odpowiadające typom zasobów, których chcesz użyć w projekcie, zgodnie z opisem w poniższej tabeli:

    |Typ elementu zawartości|Nazwa dostosowywania kompilacji|
    |----------------| - |
    |Tekstury i obrazy|**ImageContentTask(.targets, .props)**|
    |Modele 3D|**MeshContentTask(.targets, .props)**|
    |Programy do cieniowania|**ShaderGraphContentTask(.targets, .props)**|

3. Wybierz przycisk **OK.**

## <a name="include-assets-in-your-build"></a>Uwzględnianie zasobów w kompilacji

Teraz, gdy projekt wie o różnych rodzajach zasobów 3D, które chcesz użyć, następnym krokiem jest poinformowanie go, które pliki są zasobami 3D i jakie są ich zasoby.

### <a name="to-add-an-asset-to-your-build"></a>Aby dodać zasób do kompilacji

1. W **Eksploratorze rozwiązań**w projekcie otwórz menu skrótów zasobu, a następnie wybierz polecenie **Właściwości**.

   Zostanie wyświetlone okno dialogowe **Strona właściwości** zasobu.

2. Upewnij się, że **konfiguracja** i **platforma** właściwości są ustawione na wartości, do których chcesz zastosować zmiany.

3. W obszarze **Właściwości konfiguracji**wybierz pozycję **Ogólne**, a następnie w siatce właściwości w obszarze **Ogólne**ustaw właściwość **Typ elementu** na odpowiedni typ elementu potoku zawartości. Na przykład dla pliku obrazu lub tekstury wybierz polecenie **Potok zawartości obrazu**.

    > [!IMPORTANT]
    > Domyślnie visual studio zakłada, że wiele rodzajów plików obrazów powinny być podzielone na kategorie przy użyciu typu elementu **image,** który jest wbudowany w programie Visual Studio. W związku z tym należy zmienić **element typ** właściwości każdego obrazu, który ma być przetwarzany przez potok zawartości obrazu. Inne typy plików źródłowych potoku zawartości dla modeli 3D i grafiki wizualnej modułu cieniującego domyślnie do **poprawnego typu elementu**.

4. Wybierz przycisk **OK.**

Poniżej przedstawiono trzy typy elementów potoku zawartości i skojarzone z nimi typy plików źródłowych i wyjściowych.

|Typ towaru|Typy plików źródłowych|Format pliku wyjściowego|
|---------------| - | - |
|**Potok zawartości obrazu**|Przenośna grafika sieciowa (*.png*)<br /><br /> JPEG (*.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Powierzchnia bezpośredniego rysowania (*.dds*)<br /><br /> Format wymiany grafiki (*.gif*)<br /><br /> Bitmapa (*.bmp*, *.dib*)<br /><br /> Format pliku obrazu z tagiem (*.tif*, *.tiff*)<br /><br /> Targa (*.tga*)|Powierzchnia DirectDraw (*.dds*)|
|**Potok zawartości siatki**|AutoDesk FBX Plik wymiany (*.fbx*)<br /><br /> Collada DAE Plik (*.dae*)<br /><br /> Wavefront OBJ Plik (*.obj*)|Plik siatki 3D (*.cmo*)|
|**Potok zawartości modułu cieniującego**|Wizualny wykres modułu cieniującego (*.dgsl*)|Skompilowane wyjście modułu cieniującego (*.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Konfigurowanie właściwości potoku zawartości zasobów

Można ustawić właściwości potoku zawartości każdego pliku zasobów, tak aby został zbudowany w określony sposób.

### <a name="to-configure-content-pipeline-properties"></a>Aby skonfigurować właściwości potoku zawartości

1. W **Eksploratorze rozwiązań**w projekcie otwórz menu **skrótów**dla pliku zasobu, a następnie wybierz polecenie Właściwości .

   Zostanie wyświetlone okno dialogowe **Strona właściwości** zasobu.

2. Upewnij się, że **konfiguracja** i **platforma** właściwości są ustawione na wartości, które mają być stosowane do zmian.

3. W obszarze **Właściwości konfiguracji**wybierz węzeł potoku zawartości (na przykład Potok **zawartości obrazu** dla zasobów tekstury i obrazu), a następnie w siatce właściwości ustaw właściwości na odpowiednie wartości. Na przykład, aby wygenerować mipmaps dla zasobu tekstury w czasie kompilacji, ustaw **właściwość Generuj mips** na **Tak**.

4. Wybierz przycisk **OK.**

### <a name="image-content-pipeline-configuration"></a>Konfiguracja potoku zawartości obrazu

Korzystając z narzędzia potoku zawartości obrazu do tworzenia zasobu tekstury, można skompresować teksturę na różne sposoby, wskazać, czy poziomy MIP powinny być generowane w czasie kompilacji, i zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Kompresji**|Określa typ kompresji używany dla pliku wyjściowego.<br /><br /> Dostępne są następujące opcje:<br /><br /> -   **Brak kompresji**<br />-   **kompresja BC1_UNORM**<br />-   **kompresja BC1_UNORM_SRGB**<br />-   **kompresja BC2_UNORM**<br />-   **kompresja BC2_UNORM_SRGB**<br />-   **kompresja BC3_UNORM**<br />-   **kompresja BC3_UNORM_SRGB**<br />-   **Kompresja BC4_UNORM**<br />-   **kompresja BC4_SNORM**<br />-   **kompresja BC5_UNORM**<br />-   **Kompresja BC5_SNORM**<br />-   **kompresja BC6H_UF16**<br />-   **kompresja BC6H_SF16**<br />-   **Kompresja BC7_UNORM**<br />-   **kompresja BC7_UNORM_SRGB**<br /><br /> Aby uzyskać informacje o tym, które formaty kompresji są obsługiwane w różnych wersjach programu DirectX, zobacz [Przewodnik po programowaniu dla DXGI](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews).|
|Konwertowanie na wstępnie pomnożony format alfa|**Tak,** aby przekonwertować obraz na wstępnie pomnożony format alfa w pliku wyjściowym; w przeciwnym razie **nie**. Tylko plik wyjściowy zostanie zmieniony, obraz źródłowy pozostaje niezmieniony.|
|**Generowanie mips**|**Tak,** aby wygenerować pełny łańcuch MIP w czasie kompilacji i uwzględnić go w pliku wyjściowym; w przeciwnym razie **nie**. Jeśli **nie**, a plik źródłowy zawiera już łańcuch mipmap, plik wyjściowy będzie miał łańcuch MIP; w przeciwnym razie plik wyjściowy nie będzie miał łańcucha MIP.|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego nie ma wpływu na jego format pliku.|

### <a name="mesh-content-pipeline-configuration"></a>Konfiguracja potoku zawartości siatki

Podczas tworzenia zasobu siatki za pomocą narzędzia do potoku zawartości siatki można zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego nie ma wpływu na jego format pliku.|

### <a name="shader-content-pipeline-configuration"></a>Konfiguracja potoku zawartości modułu cieniującego

Korzystając z narzędzia potoku zawartości modułu cieniującego do zbudowania zasobu modułu cieniującego, można zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego nie ma wpływu na jego format pliku.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Ładowanie i używanie zasobów 3D w czasie wykonywania

### <a name="use-textures-and-images"></a>Używanie tekstur i obrazów

Direct3D udostępnia funkcje tworzenia zasobów tekstur. W direct3D 11 biblioteka narzędzi D3DX11 udostępnia dodatkowe funkcje tworzenia zasobów tekstur i widoków zasobów bezpośrednio z plików obrazów. Aby uzyskać więcej informacji na temat tworzenia zasobu tekstury w funkcji Direct3D 11, zobacz [Tekstury](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures). Aby uzyskać więcej informacji na temat używania biblioteki D3DX11 do tworzenia zasobu tekstury lub widoku zasobów z pliku obrazu, zobacz [Jak: Zainicjowanie tekstury z pliku](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to).

### <a name="use-3d-models"></a>Korzystanie z modeli 3D

Direct3D 11 nie udostępnia funkcji do tworzenia zasobów z modeli 3D. Zamiast tego należy napisać kod, który odczytuje plik modelu 3D i tworzy bufory wierzchołków i indeksów, które reprezentują model 3D i wszelkie zasoby, których wymaga model — na przykład tekstury lub moduły cieniowania.

### <a name="use-shaders"></a>Korzystanie z modułów cieniującego

Direct3D udostępnia funkcje tworzenia zasobów modułu cieniującego i wiązania ich z programowalnym potokiem grafiki. Aby uzyskać więcej informacji na temat tworzenia zasobu modułu cieniującego w programie Direct3D i powiązania go z potokiem, zobacz [Przewodnik programowania dla HLSL](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide).

W potoku grafiki programowalne każdy etap potoku musi dać następny etap potoku wynik, który jest sformatowany w sposób, który może zrozumieć. Ponieważ Projektant modułu cieniującego może tworzyć tylko moduły cieniowania pikseli, oznacza to, że aplikacja musi być dostępna w celu zapewnienia, że dane, które otrzymuje, są w oczekiwanym formacie. Przed modułem cieniowania pikseli i wykonywaniem przekształceń geometrycznych występuje kilka programowalnych etapów modułu cieniującego — moduł cieniujący wierzchołków, moduł cieniujący kadłuba, moduł cieniujący domeny i moduł cieniujący geometrię. Nieprogramowalny etap tesselacji występuje również przed modułem cieniowania pikseli. Bez względu na to, który z tych etapów bezpośrednio poprzedza moduł cieniujący pikseli, musi on podać jego wynik w tym formacie:

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

W zależności od węzłów Projektanta modułu cieniującego używanych w modułie cieniującym może być również konieczne podanie dodatkowych danych w formacie zgodnie z tymi definicjami:

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Jak: Eksportowanie tekstury zawierającej mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|W tym artykule opisano sposób eksportowania tekstury zawierającej wstępnie skomputione mipmaps za pomocą potoku zawartości obrazu.|
|[Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|W tym artykule opisano sposób eksportowania tekstury zawierającej wstępniemulowane wartości alfa za pomocą potoku zawartości obrazu.|
|[Jak: Eksportowanie tekstury do użytku z aplikacjami Direct2D lub JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|W tym artykule opisano sposób eksportowania tekstury, która może być używana w aplikacji Direct2D lub JavaScript za pomocą potoku zawartości obrazu.|
|[Praca z zasobami 3D w grach i aplikacjach](../designers/working-with-3-d-assets-for-games-and-apps.md)|W tym artykule opisano narzędzia do edycji, które program Visual Studio zapewnia do tworzenia i manipulowania zasobami 3D, które obejmują tekstury i obrazy, modele 3D i moduły cieniujące.|
|[Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)|W tym artykule opisano sposób eksportowania modułu cieniującego z Projektanta modułu cieniującego.|
