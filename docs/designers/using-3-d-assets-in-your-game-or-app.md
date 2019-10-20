---
title: Korzystanie z zasobów 3W w grach lub aplikacji
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 400e69ddaf9ebd3596edf3b926484b623225d672
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634534"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Instrukcje: korzystanie z zasobów 3D w grach lub aplikacjach

W tym artykule opisano, jak można użyć programu Visual Studio do przetwarzania zasobów 3D i uwzględniania ich w kompilacjach.

Po użyciu narzędzi w programie Visual Studio do tworzenia zasobów 3D następnym krokiem jest użycie ich w aplikacji. Jednak zanim będzie można korzystać z nich, zasoby muszą zostać przekształcone w format, który może być zrozumiały dla technologii DirectX. Aby ułatwić transformację elementów zawartości, program Visual Studio udostępnia dostosowania kompilacji dla każdego rodzaju elementu zawartości, który może wyprodukować. Aby uwzględnić zasoby w kompilacji, wystarczy skonfigurować projekt do korzystania z dostosowań kompilacji, dodać zasoby do projektu i skonfigurować zasoby do korzystania z poprawnego dostosowania kompilacji. Następnie można załadować zasoby do aplikacji i użyć ich przez tworzenie i wypełnianie zasobów DirectX tak samo jak w przypadku dowolnej innej aplikacji DirectX.

## <a name="configure-your-project"></a>Konfigurowanie projektu

Aby można było wdrożyć zasoby 3W w ramach kompilacji, program Visual Studio musi wiedzieć o typach zasobów, które mają zostać wdrożone. Program Visual Studio już wie o wielu wspólnych typach plików, ale ponieważ tylko niektóre aplikacje używają zasobów 3W, program Visual Studio nie zakłada, że projekt będzie kompilować te rodzaje plików. Możesz powiedzieć programowi Visual Studio, że aplikacja używa tych rodzajów zasobów przy użyciu *dostosowań kompilacji*— pliki, które poinformują program Visual Studio, jak przetwarzać różne typy plików w sposób przydatny, które są dostępne dla każdego typu zasobu. Ponieważ te dostosowania są stosowane do poszczególnych projektów, wystarczy dodać odpowiednie dostosowania do projektu.

### <a name="to-add-the-build-customizations-to-your-project"></a>Aby dodać dostosowania kompilacji do projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz pozycję **kompilacja zależności**  > **dostosowania kompilacji**.

   Zostanie wyświetlone okno dialogowe **pliki dostosowania kompilacji wizualizacji C++**  .

2. W obszarze **dostępne pliki dostosowania kompilacji**zaznacz pola wyboru odpowiadające typom zasobów, które mają być używane w projekcie, zgodnie z opisem w poniższej tabeli:

    |Typ elementu zawartości|Nazwa dostosowania kompilacji|
    |----------------| - |
    |Tekstury i obrazy|**ImageContentTask (. targets,. props)**|
    |Modele 3W|**MeshContentTask (. targets,. props)**|
    |Programy do cieniowania|**ShaderGraphContentTask (. targets,. props)**|

3. Wybierz przycisk **OK** .

## <a name="include-assets-in-your-build"></a>Uwzględnij zasoby w kompilacji

Teraz, gdy Twój projekt wie o różnych typach zasobów 3W, które mają być używane, następnym krokiem jest poinformowanie o tym, które pliki są zasobami 3W i jakie rodzaje zasobów są im.

### <a name="to-add-an-asset-to-your-build"></a>Aby dodać element zawartości do kompilacji

1. W **Eksplorator rozwiązań**w projekcie Otwórz menu skrótów elementu zawartości, a następnie wybierz polecenie **Właściwości**.

   Zostanie wyświetlone okno dialogowe **Strona właściwości** zasobu.

2. Upewnij się, że właściwości **konfiguracji** i **platformy** są ustawione na wartości, do których mają zostać zastosowane zmiany.

3. W obszarze **Właściwości konfiguracji**wybierz opcję **Ogólne**, a następnie w siatce właściwości w obszarze **Ogólne**ustaw właściwość **Typ elementu** na odpowiedni typ elementu potoku zawartości. Na przykład dla pliku obrazu lub tekstury wybierz pozycję **potok zawartości obrazu**.

    > [!IMPORTANT]
    > Domyślnie program Visual Studio zakłada, że wiele rodzajów plików obrazów należy klasyfikować przy użyciu typu elementu **obrazu** wbudowanego w program Visual Studio. W związku z tym należy zmienić właściwość **typu elementu** dla każdego obrazu, który ma być przetwarzany przez potok zawartości obrazu. Inne typy plików źródłowych potoku zawartości dla modeli 3D i grafiki programu Visual Shader są domyślne dla poprawnego **typu elementu**.

4. Wybierz przycisk **OK** .

Poniżej przedstawiono trzy typy elementów potoku zawartości i skojarzone z nimi typy plików źródłowych i wyjściowych.

|Typ elementu|Typy plików źródłowych|Format pliku wyjściowego|
|---------------| - | - |
|**Potok zawartości obrazów**|Portable Network Graphics ( *. png*)<br /><br /> JPEG ( *. jpg*, *. jpeg*, *. jpe*, *. JFIF*)<br /><br /> Bezpośrednie rysowanie powierzchni ( *. DDS*)<br /><br /> Graphics Interchange Format ( *. gif*)<br /><br /> Mapa bitowa ( *. bmp*, *. dib*)<br /><br /> Tagged Image File Format ( *. tif*, *. TIFF*)<br /><br /> Targa ( *. tga*)|Powierzchnia DirectDraw ( *. DDS*)|
|**Potok zawartości siatki**|Plik FBX Interchange ( *. FBX*)<br /><br /> Plik DAE formacie Collada ( *. DAE*)<br /><br /> Plik OBJ plik Wavefront ( *. obj*)|plik siatki 3D ( *. marketingu*)|
|**Potok zawartości programu do cieniowania**|Graf cieniowania wizualnego ( *. dgsl*)|Skompilowane dane wyjściowe modułu cieniującego ( *. CSO*)|

## <a name="configure-asset-content-pipeline-properties"></a>Konfigurowanie właściwości potoku zawartości zasobów

Można ustawić właściwości potoku zawartości dla każdego pliku zasobów, aby można było go skompilować w określony sposób.

### <a name="to-configure-content-pipeline-properties"></a>Aby skonfigurować właściwości potoku zawartości

1. W **Eksplorator rozwiązań**w projekcie Otwórz menu skrótów dla pliku zasobów, a następnie wybierz polecenie **Właściwości**.

   Zostanie wyświetlone okno dialogowe **Strona właściwości** zasobu.

2. Upewnij się, że właściwości **konfiguracji** i **platformy** są ustawione na wartości, do których mają zostać zastosowane zmiany.

3. W obszarze **Właściwości konfiguracji**wybierz węzeł potoku zawartości (na przykład **potok zawartości obrazu** dla tekstury i zasobów obrazu), a następnie w siatce właściwości ustaw odpowiednie wartości właściwości. Na przykład, aby wygenerować mipmapy dla elementu zawartości tekstury w czasie kompilacji, należy ustawić właściwość **Generuj MIPS** na **wartość tak**.

4. Wybierz przycisk **OK** .

### <a name="image-content-pipeline-configuration"></a>Konfiguracja potoku zawartości obrazu

Korzystając z narzędzia potoku zawartości obrazów do tworzenia zasobów tekstury, można skompresować teksturę na różne sposoby, wskazać, czy poziomy MIP mają być generowane w czasie kompilacji, i zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Kompresuj**|Określa typ kompresji, który jest używany dla pliku wyjściowego.<br /><br /> Dostępne opcje to:<br /><br /> -   **bez kompresji**<br />-   **kompresję BC1_UNORM**<br />-   **kompresję BC1_UNORM_SRGB**<br />-   **kompresję BC2_UNORM**<br />-   **kompresję BC2_UNORM_SRGB**<br />-   **kompresję BC3_UNORM**<br />-   **kompresję BC3_UNORM_SRGB**<br />-   **kompresję BC4_UNORM**<br />-   **kompresję BC4_SNORM**<br />-   **kompresję BC5_UNORM**<br />-   **kompresję BC5_SNORM**<br />-   **kompresję BC6H_UF16**<br />-   **kompresję BC6H_SF16**<br />-   **kompresję BC7_UNORM**<br />-   **kompresję BC7_UNORM_SRGB**<br /><br /> Aby uzyskać informacje o tym, które formaty kompresji są obsługiwane w różnych wersjach programu DirectX, zobacz [Przewodnik programowania dla infrastruktury dxgi](http://go.microsoft.com/fwlink/p/?LinkId=246265).|
|Konwertuj na wstępnie przemnożony format alfa|**Tak** , aby przekonwertować obraz na wstępnie przemnożony format alfa w pliku wyjściowym; w przeciwnym razie **nie**. Tylko plik wyjściowy zostanie zmieniony, obraz źródłowy nie zmieni się.|
|**Generuj MIPS**|**Wartość tak** powoduje wygenerowanie pełnego łańcucha MIP w czasie kompilacji i uwzględnienie go w pliku wyjściowym; w przeciwnym razie **nie**. Jeśli **nie**, a plik źródłowy zawiera już łańcuch mipmappingu, plik wyjściowy będzie miał łańcuch MCI; w przeciwnym razie plik wyjściowy nie będzie miał łańcucha MIP.|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego nie ma wpływu na jego format pliku.|

### <a name="mesh-content-pipeline-configuration"></a>Konfiguracja potoku zawartości siatki

Korzystając z narzędzia potoku zawartości siatki do tworzenia zasobów siatki, można zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego nie ma wpływu na jego format pliku.|

### <a name="shader-content-pipeline-configuration"></a>Konfiguracja potoku zawartości programu do cieniowania

Korzystając z narzędzia potoku zawartości programu do cieniowania, można zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Dane wyjściowe zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego nie ma wpływu na jego format pliku.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Ładowanie i używanie zasobów 3W w czasie wykonywania

### <a name="use-textures-and-images"></a>Używanie tekstur i obrazów

Direct3D oferuje funkcje do tworzenia zasobów tekstury. W programie Direct3D 11 biblioteka narzędzi D3DX11 udostępnia dodatkowe funkcje do tworzenia zasobów tekstury i widoków zasobów bezpośrednio z plików obrazów. Aby uzyskać więcej informacji na temat sposobu tworzenia zasobu tekstury w programie Direct3D 11, zobacz [tekstury](http://go.microsoft.com/fwlink/p/?LinkID=246267). Aby uzyskać więcej informacji na temat używania biblioteki D3DX11 do tworzenia zasobów tekstury lub widoku zasobów na podstawie pliku obrazu, zobacz [How to: Initialize a Texture from a File](http://go.microsoft.com/fwlink/p/?LinkId=246268).

### <a name="use-3d-models"></a>Korzystanie z modeli 3D

Program Direct3D 11 nie udostępnia funkcji służących do tworzenia zasobów z modeli 3W. Zamiast tego należy napisać kod, który odczytuje plik modelu 3D i tworzy Bufory wierzchołków i indeksów reprezentujące model 3D i wszystkie zasoby wymagane przez model — na przykład tekstury lub cieniowania.

### <a name="use-shaders"></a>Używanie programów do cieniowania

Direct3D oferuje funkcje do tworzenia zasobów programu do cieniowania i wiązania ich z programowalnym potokiem grafiki. Aby uzyskać więcej informacji na temat sposobu tworzenia zasobu modułu cieniującego w programie Direct3D i powiązania go z potokiem, zobacz [Przewodnik programowania dla HLSL](http://go.microsoft.com/fwlink/p/?LinkID=261521).

W przypadku programowalnego potoku grafiki każdy etap potoku musi przydzielić do następnego etapu potoku wynik sformatowany w sposób, który może zrozumieć. Ponieważ projektant programu do cieniowania może tworzyć tylko cieniowanie pikseli, oznacza to, że jest to aplikacja, aby upewnić się, że odebrane dane są w oczekiwanym formacie. Kilka programowalnych etapów modułu cieniującego występuje przed cieniowanie pikseli i wykonywanie transformacji geometrycznych — cieniowania wierzchołków, cieniowania kadłuba, cieniowania domeny i cieniowania geometrycznego. Nieprogramowalny etap mozaikowania również występuje przed cieniowanie pikseli. Niezależnie od tego, który z tych etapów bezpośrednio poprzedza cieniowanie pikseli, musi podać swój wynik w tym formacie:

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

W zależności od węzłów projektanta modułu cieniującego, które są używane w module cieniującego, może być również konieczne podanie dodatkowych danych w formacie zgodnie z tymi definicjami:

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

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: eksportowanie tekstury zawierającej mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Opisuje sposób użycia potoku zawartości obrazu do wyeksportowania tekstury zawierającej wstępnie obliczony mipmapy.|
|[Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Opisuje sposób użycia potoku zawartości obrazu do wyeksportowania tekstury zawierającej wstępnie przemnożone wartości alfa.|
|[Instrukcje: eksportowanie tekstury do użycia z aplikacjami Direct2D lub JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Opisuje sposób użycia potoku zawartości obrazu do wyeksportowania tekstury, która może być używana w aplikacji Direct2D lub JavaScript.|
|[Praca z zasobami 3W dla gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Opisuje narzędzia do edycji, które program Visual Studio zapewnia do tworzenia i manipulowania zasobami 3W, w tym tekstury i obrazy, modele 3W i programy do cieniowania.|
|[Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)|Opisuje sposób eksportowania programu do cieniowania z projektanta cieniowania.|