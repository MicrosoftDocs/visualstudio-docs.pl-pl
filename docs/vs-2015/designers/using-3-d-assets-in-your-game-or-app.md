---
title: Używanie obiektów 3-d w grach i aplikacjach | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ca0150b44bbed9f411af25c5ce3805e553e8272
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54775114"
---
# <a name="using-3-d-assets-in-your-game-or-app"></a>Korzystanie z obiektów 3-D w grach i aplikacjach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym artykule opisano, jak można użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do przetwarzania zasobów 3D i zawierania ich w kompilacji.  
  
 Po użyciu narzędzi dostępnych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do utworzenia zasobów 3-D następnym krokiem jest ich używać w aplikacji. Jednak zanim można ich używać, obiekty muszą zostać przekształcone do formatu, który może zrozumieć program DirectX. Aby ułatwić przekształcenie zasobów, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zawiera dostosowania kompilacji dla każdego rodzaju zasobów, które może wygenerować. Aby uwzględnić zasoby w kompilacji, trzeba będzie skonfigurować projekt do używania dostosowań kompilacji, dodać zasoby do projektu i konfigurowanie zasobów do użycia poprawnego dostosowywania kompilacji. Po tym można załadować zasoby do aplikacji i ich używać, tworząc i wypełniając zasoby DirectX tak jak w przypadku innych aplikacji DirectX.  
  
## <a name="configuring-your-project"></a>Konfigurowanie projektu  
 Przed rozpoczęciem wdrażania zasobów 3-D, jako część kompilacji, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] musi poznać rodzaje obiektów, które mają zostać wdrożone. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] już zna wiele popularnych typów plików, ale ponieważ tylko niektóre rodzaje aplikacji używają zasobów 3-D, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie zakłada, że projekt utworzy te rodzaje plików. Można stwierdzić [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] że aplikacja używa tych rodzajów zasobów przy użyciu *lacji*— pliki, które informują [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sposób przetwarzania różnych typów plików w wygodny sposób — które są dostarczane dla każdego typu zasobu. Ponieważ te dostosowania są stosowane w poszczególnych projektów, trzeba będzie dodać odpowiednie dostosowania do projektu.  
  
#### <a name="to-add-the-build-customizations-to-your-project"></a>Aby dodać dostosowania kompilacji do projektu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **zależności kompilacji**, **dostosowania kompilacji**. **Pliki z dostosowywania kompilacji Visual C++** zostanie wyświetlone okno dialogowe.  
  
2.  W obszarze **dostępne pliki dostosowania kompilacji**, zaznacz pole wyboru, które odpowiadają typom zasobów, które chcesz użyć w projekcie, zgodnie z opisem w poniższej tabeli:  
  
    |Typ zasobu|Nazwa dostosowania kompilacji|  
    |----------------|------------------------------|  
    |Obrazami i teksturami|**ImageContentTask(.targets, .props)**|  
    |Modele 3-D|**MeshContentTask (.targets, .props)**|  
    |Programy do cieniowania|**ShaderGraphContentTask(.targets, .props)**|  
  
3.  Wybierz **OK** przycisku.  
  
## <a name="including-assets-in-your-build"></a>Dołączanie zasobów w kompilacji  
 Teraz, gdy projektu wie o różnych rodzajów zasobów 3-D, których chcesz użyć, następnym krokiem jest stwierdzenie, pliki, które są zasobów 3-D, i jakie typy zasobów są.  
  
#### <a name="to-add-an-asset-to-your-build"></a>Aby dodać składnik aktywów do kompilacji  
  
1. W **Eksploratora rozwiązań**w swoim projekcie Otwórz menu skrótów elementu zawartości, a następnie wybierz **właściwości**. Zasób **strona właściwości** zostanie wyświetlone okno dialogowe.  
  
2. Upewnij się, że **konfiguracji** i **platformy** właściwości są ustawione na wartości, które mają zostać zastosowane do zmiany.  
  
3. W obszarze **właściwości konfiguracji**, wybierz **ogólne**, a następnie w siatce właściwości w obszarze **ogólne**ustaw **typu elementu** właściwości typem elementu potoku zawartości. Na przykład pliku obrazu lub tekstury wybierz **potok zawartości obrazu**.  
  
   > [!IMPORTANT]
   >  Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przyjęto założenie, że wiele rodzajów plików obrazu należy podzielić na kategorie za pomocą **obraz** typu, która jest wbudowana w elementu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W związku z tym, należy zmienić **typu elementu** właściwość każdego obrazu, który ma być przetwarzany przez potok zawartości obrazu. Inne typy zawartości potoku pliki źródłowe dla modeli 3D i wizualnego modułu cieniującego grafiki domyślnie poprawny **typu elementu**.  
  
4. Wybierz **OK** przycisku.  
  
   Oto trzy typy elementów potoku zawartości i ich skojarzone źródło i dane wyjściowe typów plików.  
  
|Typ elementu|Typy plików źródłowych|Format pliku wyjściowego|  
|---------------|-----------------------|------------------------|  
|**Potok zawartości obrazu**|Portable Network Graphics (PNG)<br /><br /> JPEG (.jpg, .jpeg, .jpe, .jfif)<br /><br /> Bezpośrednie powierzchni rysowania (.dds)<br /><br /> Plik tekstowy w formacie GIF (.gif)<br /><br /> Mapa bitowa (.bmp, .dib)<br /><br /> Plik TIFF (.tif, .tiff)<br /><br /> Targa (.tga)|Powierzchnia DirectDraw (.dds)|  
|**Potok zawartości siatki**|AutoDesk FBX Interchange File (.fbx)<br /><br /> Plik Collada DAE (.dae)<br /><br /> Plik OBJ czoła fali (.obj)|Plik siatki 3-D (.cmo)|  
|**Potok zawartości programu do cieniowania**|Wizualny wykres modułu cieniującego (.dgsl)|Skompilowane dane wyjściowe cieniowania (.cso)|  
  
## <a name="configuring-asset-content-pipeline-properties"></a>Konfigurowanie właściwości potoku zawartości zasobów  
 Można ustawić właściwości potoku zawartości każdego pliku zasobów, dzięki czemu zostanie skompilowany w określony sposób.  
  
#### <a name="to-configure-content-pipeline-properties"></a>Aby skonfigurować właściwości potoku zawartości  
  
1.  W **Eksploratora rozwiązań**w swoim projekcie Otwórz menu skrótów dla pliku zasobów, a następnie wybierz **właściwości**. Zasób **strona właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  Upewnij się, że **konfiguracji** i **platformy** właściwości są ustawione na wartości, które mają zostać zastosowane do zmiany.  
  
3.  W obszarze **właściwości konfiguracji**, wybierz węzeł potoku zawartości — na przykład **potok zawartości obrazu** dla tekstur i obrazów — a następnie w siatce właściwości ustaw właściwości odpowiednie wartości. Na przykład, aby wygenerować mapy MIP dla trwałego tekstura w czasie kompilacji, należy ustawić **Generuj Mips** właściwości **tak**.  
  
4.  Wybierz **OK** przycisku.  
  
### <a name="image-content-pipeline-configuration"></a>Konfiguracja potoku zawartości obrazów  
 Korzystając z narzędzia potoku zawartości obrazu do tworzenia zasobów tekstury, można kompresować tekstury na różne sposoby, wskazywać, czy poziomy MCI powinny być generowane w czasie kompilacji, a następnie zmień nazwę pliku wyjściowego.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Kompresuj**|Określa typ kompresji, który jest używany dla pliku wyjściowego.<br /><br /> Dostępne opcje to:<br /><br /> -   **Bez kompresji**<br />-   **Kompresja bc1_unorm**<br />-   **Kompresja bc1_unorm_srgb**<br />-   **Kompresja bc2_unorm**<br />-   **Kompresja bc2_unorm_srgb**<br />-   **Kompresja bc3_unorm**<br />-   **Kompresja bc3_unorm_srgb**<br />-   **Kompresja bc4_unorm**<br />-   **Kompresja bc4_snorm**<br />-   **Kompresja bc5_unorm**<br />-   **Kompresja bc5_snorm**<br />-   **Kompresja bc6h_uf16**<br />-   **Kompresja bc6h_sf16**<br />-   **Kompresja bc7_unorm**<br />-   **Kompresja bc7_unorm_srgb**<br /><br /> Aby uzyskać informacje o kompresji formaty są obsługiwane w różnych wersjach programu DirectX, zobacz [przewodnik programowania w infrastrukturze dxgi](http://go.microsoft.com/fwlink/p/?LinkId=246265).|  
|Konwertuj na wstępnie przemnożonego alfa formatu|**Tak** konwersji obrazu wstępnie przemnożonego alfa format w pliku wyjściowym; w przeciwnym razie **nie**. Tylko plik wyjściowy zostanie zmieniony, obraz źródłowy pozostaje niezmieniony.|  
|**Generuj Mips**|**Tak** do generowania pełnego łańcucha MIP w czasie kompilacji i uwzględnić go w pliku wyjściowym; w przeciwnym razie **nie**. Jeśli **nie**, a plik źródłowy zawiera już łańcuch mipmappingu, plik wyjściowy będzie zawierał łańcuch MIP; w przeciwnym wypadku plik wyjściowy będzie zawierał żadnego łańcucha MIP.|  
|**Wyjście zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego pliku nie ma wpływu na jego format pliku.|  
  
### <a name="mesh-content-pipeline-configuration"></a>Konfiguracja potoku zawartości siatki  
 Gdy używasz narzędzia potoku zawartości siatki do tworzenia zawartości siatki można zmienić nazwę pliku wyjściowego.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Wyjście zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego pliku nie ma wpływu na jego format pliku.|  
  
### <a name="shader-content-pipeline-configuration"></a>Konfiguracja potoku zawartości modułu cieniującego  
 Korzystając z narzędzia potoku zawartości modułu cieniującego do tworzenia zasobów programu do cieniowania, możesz zmienić nazwę pliku wyjściowego.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Wyjście zawartości**|Określa nazwę pliku wyjściowego. **Ważne:**  Zmiana rozszerzenia nazwy pliku wyjściowego pliku nie ma wpływu na jego format pliku.|  
  
## <a name="loading-and-using-3-d-assets-at-run-time"></a>Ładowanie i używanie obiektów 3-d w czasie wykonywania  
  
### <a name="using-textures-and-images"></a>Używanie obrazów i tekstur  
 Program Direct3D oferuje funkcje tworzenia zasobów tekstur. W interfejsie Direct3D 11 Biblioteka narzędzi D3DX11 oferuje dodatkowe funkcje tworzenia zasobów tekstury i widoków zasobów bezpośrednio z plików obrazu. Aby uzyskać więcej informacji na temat sposobu tworzenia zasobu tekstury w interfejsie Direct3D 11, zobacz [tekstury](http://go.microsoft.com/fwlink/p/?LinkID=246267). Aby uzyskać więcej informacji o sposobie używania biblioteki D3DX11 do utworzenia zasobu tekstury lub widoku zasobu z pliku obrazu, zobacz [jak: Inicjowanie tekstury z pliku](http://go.microsoft.com/fwlink/p/?LinkId=246268).  
  
### <a name="using-3-d-models"></a>Przy użyciu modeli 3D  
 Direct3D 11 nie zapewnia funkcji tworzenia zasobów z modelami 3-D. Zamiast tego trzeba napisać kod, który odczytuje plik modelu 3-D i tworzy bufory wierzchołków i indeksów, które reprezentują 3-D model i wszystkie zasoby, których wymaga model — na przykład tekstury lub cieniowania.  
  
### <a name="using-shaders"></a>Używanie modułów cieniujących  
 Direct3D oferuje funkcje służące do tworzenia zasobów cieniowania i powiązania ich z rurociągiem programowanej grafiki. Aby uzyskać więcej informacji na temat sposobu tworzenia zasobu modułu cieniującego w interfejsie Direct3D i powiązania z potokiem, zobacz [przewodnik programowania w języku hlsl](http://go.microsoft.com/fwlink/p/?LinkID=261521).  
  
 W potoku programowanej grafiki każdy etap potoku musi dawać do kolejnego etapu potoku wynik, który jest sformatowany w sposób, który może zrozumieć. Ponieważ program Shader Designer może tworzyć tylko cieniowania pikseli, oznacza to, że to do aplikacji, aby upewnij się, że dane, które otrzymuje w formacie, którego oczekuje. Kilka programowalnych etapów modułu cieniującego występuje przed modułem do cieniowania pikseli i dokonuje przekształceń geometrycznych — moduł cieniujący wierzchołków, moduł cieniujący kadłuba, moduł cieniujący domeny i moduł cieniujący geometrii. Etap kafelkowania programowania występuje również przed modułem do cieniowania pikseli. Niezależnie od tego, który z tych etapów bezpośrednio poprzedza cieniowanie pikseli musi podać swój wynik w następującym formacie:  
  
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
  
 W zależności od węzłów programu Shader Designer używanych w cieniowaniu, użytkownik może być również konieczne podane dodatkowych danych w formacie zgodnym z tymi definicjami:  
  
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
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Eksportowanie tekstury zawierającej mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Informacje dotyczące używania potoku zawartości obrazu do wyeksportowania tekstury, które zawierają wstępnie obliczone mipmapy.|  
|[Instrukcje: Eksportowanie tekstury wykorzystującej wstępnie przemnożony kanał alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Informacje dotyczące używania potoku zawartości obrazu do eksportowania tekstur, które zawierają wstępnie przemnożone wartości alfa.|  
|[Instrukcje: Eksportowanie tekstury do użycia z Direct2D lub aplikacjami JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Informacje dotyczące używania potoku zawartości obrazu do wyeksportowania tekstury, które mogą być używane w aplikacji Direct2D lub JavaScript.|  
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Opisuje narzędzia edycji programu Visual Studio udostępnia do tworzenia i manipulowania zestawami 3D, które obejmują tekstury i obrazy, modele 3D i programów do cieniowania.|  
|[Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)|Opisuje sposób eksportowania modułu cieniującego od projektanta modułu cieniującego.|
