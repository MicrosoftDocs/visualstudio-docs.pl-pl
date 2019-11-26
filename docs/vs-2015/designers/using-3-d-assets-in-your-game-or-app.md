---
title: Używanie zasobów 3-D w grach lub aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d838b7519b40d47b644a53befb91391fa30a664
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293142"
---
# <a name="using-3-d-assets-in-your-game-or-app"></a>Korzystanie z obiektów 3-D w grach i aplikacjach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym artykule opisano, jak można użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do przetwarzania zasobów 3-D i uwzględniania ich w kompilacjach.

 Po użyciu narzędzi w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do tworzenia zasobów 3-D następnym krokiem jest użycie ich w aplikacji. Jednak zanim będzie można z nich korzystać, Twoje zasoby muszą zostać przekształcone w format, który może być zrozumiały dla technologii DirectX. Aby ułatwić transformację zasobów, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewnia dostosowania kompilacji dla każdego rodzaju elementu zawartości, który może utworzyć. Aby uwzględnić zasoby w kompilacji, wystarczy skonfigurować projekt do korzystania z dostosowań kompilacji, dodać zasoby do projektu i skonfigurować zasoby do korzystania z poprawnego dostosowania kompilacji. Następnie można załadować zasoby do aplikacji i użyć ich przez tworzenie i wypełnianie zasobów DirectX tak samo jak w przypadku dowolnej innej aplikacji DirectX.

## <a name="configuring-your-project"></a>Konfigurowanie projektu
 Przed wdrożeniem zasobów 3-D w ramach kompilacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] należy wiedzieć o typach zasobów, które mają zostać wdrożone. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] już wie o wielu wspólnych typach plików, ale ponieważ tylko niektóre typy aplikacji używają zasobów 3-D, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie zakłada, że projekt będzie kompilować te rodzaje plików. Możesz powiedzieć, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], że aplikacja używa tych rodzajów zasobów przy użyciu *dostosowań kompilacji*— pliki, które informują [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o sposobie przetwarzania różnych typów plików w sposób przydatny, które są dostępne dla każdego typu zasobu. Ponieważ te dostosowania są stosowane do poszczególnych projektów, wystarczy dodać odpowiednie dostosowania do projektu.

#### <a name="to-add-the-build-customizations-to-your-project"></a>Aby dodać dostosowania kompilacji do projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz pozycję **zależności kompilacji**i **Utwórz dostosowania**. Zostanie wyświetlone okno dialogowe **pliki dostosowania kompilacji wizualizacji C++**  .

2. W obszarze **dostępne pliki dostosowania kompilacji**zaznacz pola wyboru odpowiadające typom zasobów, które mają być używane w projekcie, zgodnie z opisem w tej tabeli:

    |Typ elementu zawartości|Nazwa dostosowania kompilacji|
    |----------------|------------------------------|
    |Tekstury i obrazy|**ImageContentTask (. targets,. props)**|
    |Modele 3-D|**MeshContentTask (. targets,. props)**|
    |Programy do cieniowania|**ShaderGraphContentTask (. targets,. props)**|

3. Wybierz przycisk **OK** .

## <a name="including-assets-in-your-build"></a>Uwzględnianie zasobów w kompilacji
 Teraz, gdy Twój projekt wie o różnych typach zasobów 3-D, których chcesz użyć, następnym krokiem jest poinformowanie o tym, które pliki są zasobami 3-D i jakie są ich zasoby.

#### <a name="to-add-an-asset-to-your-build"></a>Aby dodać element zawartości do kompilacji

1. W **Eksplorator rozwiązań**w projekcie Otwórz menu skrótów elementu zawartości, a następnie wybierz polecenie **Właściwości**. Zostanie wyświetlone okno dialogowe **strony właściwości** zasobu.

2. Upewnij się, że właściwości **konfiguracji** i **platformy** są ustawione na wartości, do których mają zostać zastosowane zmiany.

3. W obszarze **Właściwości konfiguracji**wybierz opcję **Ogólne**, a następnie w siatce właściwości w obszarze **Ogólne**ustaw właściwość **Typ elementu** na odpowiedni typ elementu potoku zawartości. Na przykład dla pliku obrazu lub tekstury wybierz pozycję **potok zawartości obrazu**.

   > [!IMPORTANT]
   > Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zakłada, że wiele rodzajów plików obrazów należy klasyfikować przy użyciu typu elementu **obrazu** wbudowanego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W związku z tym należy zmienić właściwość **typu elementu** dla każdego obrazu, który ma być przetwarzany przez potok zawartości obrazu. Inne typy plików źródłowych potoku zawartości dla modeli trójwymiarowych i grafiki programu Visual Shader są domyślne dla poprawnego **typu elementu**.

4. Wybierz przycisk **OK** .

   Oto trzy typy elementów potoku zawartości i skojarzone z nimi typy plików źródłowych i wyjściowych.

|Typ elementu|Typy plików źródłowych|Format pliku wyjściowego|
|---------------|-----------------------|------------------------|
|**Potok zawartości obrazów**|Portable Network Graphics (. png)<br /><br /> JPEG (. jpg,. jpeg,. jpe,. JFIF)<br /><br /> Bezpośrednie rysowanie powierzchni (. DDS)<br /><br /> Graphics Interchange Format (. gif)<br /><br /> Mapa bitowa (. bmp,. dib)<br /><br /> Tagged Image File Format (. tif,. TIFF)<br /><br /> Targa (. TGA)|Powierzchnia DirectDraw (. DDS)|
|**Potok zawartości siatki**|Plik FBX Interchange (. FBX)<br /><br /> Plik DAE formacie Collada (. DAE)<br /><br /> Plik OBJ plik Wavefront (. obj)|plik siatki trójwymiarowej (. marketingu)|
|**Potok zawartości programu do cieniowania**|Graf cieniowania wizualnego (. dgsl)|Skompilowane dane wyjściowe modułu cieniującego (. CSO)|

## <a name="configuring-asset-content-pipeline-properties"></a>Konfigurowanie właściwości potoku zawartości zasobów
 Można ustawić właściwości potoku zawartości dla każdego pliku zasobów, aby można było go skompilować w określony sposób.

#### <a name="to-configure-content-pipeline-properties"></a>Aby skonfigurować właściwości potoku zawartości

1. W **Eksplorator rozwiązań**w projekcie Otwórz menu skrótów dla pliku zasobów, a następnie wybierz polecenie **Właściwości**. Zostanie wyświetlone okno dialogowe **strony właściwości** zasobu.

2. Upewnij się, że właściwości **konfiguracji** i **platformy** są ustawione na wartości, do których mają zostać zastosowane zmiany.

3. W obszarze **Właściwości konfiguracji**wybierz węzeł potoku zawartości — na przykład **potok zawartości obrazu** dla tekstury i zasobów obrazu — a następnie w siatce właściwości ustaw odpowiednie wartości właściwości. Na przykład, aby wygenerować mipmapy dla elementu zawartości tekstury w czasie kompilacji, należy ustawić właściwość **Generuj MIPS** na **wartość tak**.

4. Wybierz przycisk **OK** .

### <a name="image-content-pipeline-configuration"></a>Konfiguracja potoku zawartości obrazu
 Korzystając z narzędzia potoku zawartości obrazów do tworzenia zasobów tekstury, można skompresować teksturę na różne sposoby, wskazać, czy poziomy MIP mają być generowane w czasie kompilacji, i zmienić nazwę pliku wyjściowego.

|Właściwość|Opis|
|--------------|-----------------|
|**Kompresuj**|Określa typ kompresji, który jest używany dla pliku wyjściowego.<br /><br /> Dostępne opcje to:<br /><br /> -   **bez kompresji**<br />-   **BC1_UNORM kompresji**<br />-   **BC1_UNORM_SRGB kompresji**<br />-   **BC2_UNORM kompresji**<br />-   **BC2_UNORM_SRGB kompresji**<br />-   **BC3_UNORM kompresji**<br />-   **BC3_UNORM_SRGB kompresji**<br />-   **BC4_UNORM kompresji**<br />-   **BC4_SNORM kompresji**<br />-   **BC5_UNORM kompresji**<br />-   **BC5_SNORM kompresji**<br />-   **BC6H_UF16 kompresji**<br />-   **BC6H_SF16 kompresji**<br />-   **BC7_UNORM kompresji**<br />-   **BC7_UNORM_SRGB kompresji**<br /><br /> Aby uzyskać informacje o tym, które formaty kompresji są obsługiwane w różnych wersjach programu DirectX, zobacz [Przewodnik programowania dla infrastruktury dxgi](https://go.microsoft.com/fwlink/p/?LinkId=246265).|
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

## <a name="loading-and-using-3-d-assets-at-run-time"></a>Ładowanie i używanie zasobów 3-D w czasie wykonywania

### <a name="using-textures-and-images"></a>Używanie tekstur i obrazów
 Direct3D oferuje funkcje do tworzenia zasobów tekstury. W programie Direct3D 11 biblioteka narzędzi D3DX11 udostępnia dodatkowe funkcje do tworzenia zasobów tekstury i widoków zasobów bezpośrednio z plików obrazów. Aby uzyskać więcej informacji na temat sposobu tworzenia zasobu tekstury w programie Direct3D 11, zobacz [tekstury](https://go.microsoft.com/fwlink/p/?LinkID=246267). Aby uzyskać więcej informacji na temat używania biblioteki D3DX11 do tworzenia zasobów tekstury lub widoku zasobów na podstawie pliku obrazu, zobacz [How to: Initialize a Texture from a File](https://go.microsoft.com/fwlink/p/?LinkId=246268).

### <a name="using-3-d-models"></a>Używanie modeli trójwymiarowych
 Program Direct3D 11 nie udostępnia funkcji tworzenia zasobów z modeli trójwymiarowych. Zamiast tego należy napisać kod, który odczytuje plik modelu 3-D i tworzy Bufory wierzchołków i indeksów, które reprezentują model 3-D i wszystkie zasoby wymagane przez model — na przykład tekstury lub cieniowania.

### <a name="using-shaders"></a>Używanie programów do cieniowania
 Direct3D oferuje funkcje do tworzenia zasobów programu do cieniowania i wiązania ich z programowalnym potokiem grafiki. Aby uzyskać więcej informacji na temat sposobu tworzenia zasobu modułu cieniującego w programie Direct3D i powiązania go z potokiem, zobacz [Przewodnik programowania dla HLSL](https://go.microsoft.com/fwlink/p/?LinkID=261521).

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

```

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

|Stanowisko|Opis|
|-----------|-----------------|
|[Instrukcje: eksportowanie tekstury zawierającej mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Opisuje sposób użycia potoku zawartości obrazu do wyeksportowania tekstury zawierającej wstępnie obliczony mipmapy.|
|[Instrukcje: eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Opisuje sposób użycia potoku zawartości obrazu do wyeksportowania tekstury zawierającej wstępnie przemnożone wartości alfa.|
|[Instrukcje: eksportowanie tekstury do użycia z Direct2D lub aplikacjami JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Opisuje sposób użycia potoku zawartości obrazu do wyeksportowania tekstury, która może być używana w aplikacji Direct2D lub JavaScript.|
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Opisuje narzędzia do edycji, które program Visual Studio oferuje do tworzenia i manipulowania zasobami 3-D, które obejmują tekstury i obrazy, modele trójwymiarowe i programy do cieniowania.|
|[Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)|Opisuje sposób eksportowania programu do cieniowania z projektanta cieniowania.|
