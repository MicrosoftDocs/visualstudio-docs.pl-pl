---
title: 'Przewodnik: Tworzenie realistycznej kuli Bilardowej w 3D | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26dc068ca15de93cc2b0a3ac68b83d1d351bcad4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110599"
---
# <a name="walkthrough-creating-a-realistic-3-d-billiard-ball"></a>Przewodnik: Tworzenie realistycznej kuli Bilardowej w 3D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób tworzenia realistycznej kuli bilardowej w 3D przy użyciu programu Shader Designer i edytora obrazów w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. 3-wygląd bili odbywa się przez połączenie kilku technik cieniowania z odpowiednimi zasobami tekstury.  
  
 Ten dokument przedstawia te działania:  
  
- Tworzenie wyglądu podstawowego kuli bilardowej za pomocą kształtu i tekstury.  
  
- Dodawanie głębi przy użyciu modelu oświetlenia Lamberta.  
  
- Poprawa wyglądu podstawowego przy użyciu światła odbitego wyróżnia.  
  
- Tworzenie poczucie przestrzeni przez odzwierciedlenie otoczenia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki i umiejętności w celu przeprowadzenia tego instruktażu:  
  
- Narzędzie do składania tekstur w mapę modułu, takie jak narzędzia DirectX Texture, który znajduje się w czerwca 2010 zestawu SDK programu DirectX.  
  
- Znajomość edytora obrazów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Znajomość Shader Designer w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="creating-the-basic-appearance-with-shape-and-texture"></a>Tworzenie podstawowego wyglądu za pomocą kształtu i tekstury  
 W grafice komputerowej najbardziej podstawowymi elementami wyglądu są kształt i kolor. W symulacji komputerowej jest często używa modelu 3-D do reprezentowania kształtu obiektu rzeczywistych. Szczegóły koloru jest następnie stosowane do powierzchni modelu za pomocą mapy tekstury.  
  
 Zazwyczaj może być konieczne poproszenie wykonawcy, aby utworzył model 3-D, którego można użyć, ale ponieważ kuli bilardowej jest wspólne (kula), program Shader Designer jest już odpowiedni wbudowany model.  
  
 Kula jest domyślnym kształtem podglądu w Shader Designer; Jeśli używasz obecnie innego kształtu do podglądu modułu cieniującego, przełącz go na kulę.  
  
#### <a name="to-preview-the-shader-by-using-a-sphere"></a>Aby wyświetlić podgląd modułu cieniującego za pomocą kuli  
  
- Na pasku narzędzi Projektanta modułu cieniującego wybierz **podglądu ze sferą.**  
  
  W następnym kroku utworzysz program do cieniowania, który będzie stosował teksturę do modelu, ale najpierw należy utworzyć teksturę, która umożliwia. W tym instruktażu pokazano, jak utworzyć teksturę przy użyciu edytora obrazów, który jest częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ale można użyć dowolnego edytora obrazów, który potrafi zapisać teksturę w odpowiednim formacie.  
  
  Upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Aby utworzyć teksturę kuli bilardowej przy użyciu edytora obrazów  
  
1. Utwórz teksturę do pracy. Aby uzyskać informacje dotyczące sposobu dodawania tekstury do projektu, zobacz sekcję pierwsze kroki w [edytora obrazów](../designers/image-editor.md).  
  
2. Ustaw wielkość obrazu tak, aby jej szerokość była dwukrotnością jej wysokości; jest to konieczne ze względu na sposób, że tekstura jest zmapowana na sferyczną powierzchnię kuli bilardowej. Aby zmienić rozmiar obrazu, w **właściwości** okna, określ nowe wartości **szerokość** i **wysokość** właściwości. Na przykład Ustaw szerokość na 512 i wysokość na 256.  
  
3. Narysuj teksturę kuli bilardowej, pamiętając o tym, jak tekstura jest mapowana na sferę.  
  
    Tekstura powinna wyglądać mniej więcej tak:  
  
    ![Teksturę kuli bilardowej](../designers/media/gfx-shader-demo-billiard-art-ball-texture.png "gfx_shader_demo_billiard_art_ball_texture")  
  
4. Opcjonalnie można zmniejszyć wymogi pamięci dla danej tekstury. Możesz tworzyć, zmniejszając szerokość tekstury zgodnie z jego wysokością. Kompresuje teksturę wzdłuż jej szerokości, ale ze względu na sposób, że tekstura jest mapowana do kuli, zostanie rozszerzona, gdy Bila będzie renderowana. Po zmianie rozmiaru Tekstura powinno wyglądać następująco:  
  
    ![Teksturę kuli skompresowany do kwadratu](../designers/media/gfx-shader-demo-billiard-art-ball-texture-square.png "gfx_shader_demo_billiard_art_ball_texture_square")  
  
   Teraz można utworzyć modułu cieniującego, który zastosuje tę teksturę do modelu.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Aby utworzyć cieniowania tekstury podstawowej  
  
1. Tworzenie modułu cieniującego DGSL chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modułu cieniującego DGSL do projektu, zobacz sekcję pierwsze kroki w [Shader Designer](../designers/shader-designer.md).  
  
    Domyślnie wykres cieniowania wygląda następująco:  
  
    ![Wykres modułu cieniującego domyślne](../designers/media/gfx-shader-demo-billiard-step-0.png "gfx_shader_demo_billiard_step_0")  
  
2. Zmodyfikuj domyślne cieniowanie, aby stosowało wartość próbki tekstury do bieżącego piksela. Wykres modułu cieniującego powinien wyglądać następująco:  
  
    ![Wykres modułu cieniującego, który stosuje tekstury do obiektu](../designers/media/gfx-shader-demo-billiard-step-1.png "gfx_shader_demo_billiard_step_1")  
  
3. Zastosuj teksturę utworzoną w poprzedniej procedurze przez skonfigurowanie właściwości tekstury. Ustaw wartość **tekstury** właściwość **próbki tekstury** węzeł **Texture1**, a następnie określ plik tekstury za pomocą **Filename**właściwość **Texture1** grupy właściwości w tym samym oknie właściwości.  
  
   Aby uzyskać więcej informacji dotyczących sposobu stosowania tekstury w cieniowaniu, zobacz [jak: Tworzenie cieniowania tekstury podstawowej](../designers/how-to-create-a-basic-texture-shader.md).  
  
   Twoja Bila powinna wyglądać mniej więcej tak:  
  
   ![Zbliżenie teksturą kuli bilardowej](../designers/media/gfx-shader-demo.png "gfx_shader_demo_")  
  
## <a name="creating-depth-with-the-lambert-lighting-model"></a>Tworzenie głębi przy użyciu modelu oświetlenia Lamberta  
 Do tej pory utworzono łatwo rozpoznawalną kulę bilardową. Jednakże wydaje się płaskie i mało interesujące — bardziej jak obraz kuli bilardowej kreskówki niż przekonująca replika. Płaski wygląd wynika z prostego modułu cieniowania, który zachowuje się tak, jakby wszystkie piksele na powierzchni kuli bilardowej odbiera tę samą ilość światła.  
  
 W świecie rzeczywistym światła wydają się najjaśniejszą na powierzchniach bezpośrednio źródła światła, a mniej jasne na powierzchniach, które są pod kątem oblique do po stronie źródła światła. Jest to spowodowane energia w promieniach światła jest rozłożona na najmniejszym obszarze powierzchni, gdy powierzchnia jest skierowana bezpośrednio po stronie źródła światła. Wraz z odwracaniem przeciwną stronę względem źródła światła, ta sama ilość energii są rozproszone coraz większy obszar powierzchni. Powierzchnia skierowana od źródła światła odbiera żadnej energii świetlnej, co powoduje całkowicie ciemny wygląd. To odchylenie jasności na całej powierzchni obiektu jest ważne wskazówką wizualną, która pomaga wskazać kształt obiektu; bez niego obiekt wydaje się płaski.  
  
 W grafice komputerowej *modele oświetlenia*— uproszczone przybliżenia złożonych, rzeczywistych oświetlenia interakcje — są używane do replikowania wyglądu realnego oświetlenia. Modelu oświetlenia Lamberta różni się ilością rozproszenia odbitego światła całej powierzchni obiektu zgodnie z opisem w poprzednim akapicie. Model Lambert oświetlenia można dodać do modułu cieniującego, aby nadać bili bardziej przekonujący wygląd 3-D.  
  
#### <a name="to-add-lambert-lighting-to-your-shader"></a>Aby dodać oświetlenie Lamberta do modułu cieniującego  
  
- Zmodyfikuj cieniowanie tak, aby modulowało wartość próbki tekstury przy użyciu wartości oświetlenia Lamberta. Wykres modułu cieniującego powinien wyglądać następująco:  
  
   ![Wykres modułu cieniującego oświetlenia Lamberta dodano](../designers/media/gfx-shader-demo-billiard-step-2.png "gfx_shader_demo_billiard_step_2")  
  
- Opcjonalnie można dostosować, jak oświetlenie, konfigurując **MaterialDiffuse** właściwości wykresu cieniowanego. Aby uzyskiwać dostęp do właściwości wykresu cieniowanego, wybierz pusty obszar powierzchni projektu, a następnie zlokalizuj właściwość, do której chcesz uzyskać dostęp w **właściwości** okna.  
  
  Aby uzyskać więcej informacji na temat zastosowania oświetlenia Lambert w cieniowaniu, zobacz [jak: Tworzenie podstawowego modułu cieniującego Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).  
  
  Zastosowania oświetlenia Lamberta Bila powinna wyglądać mniej więcej tak:  
  
  ![Zbliżenie teksturą i oświetlenie kuli bilardowej](../designers/media/gfx-shader-demo-billiard-ball-2.png "gfx_shader_demo_billiard_ball_2")  
  
## <a name="enhancing-the-basic-appearance-with-specular-highlights"></a>Poprawa wyglądu podstawowego przy użyciu światła odbitego  
 Model oświetlenia Lambert zapewnia poczucie kształtu i wymiarów, którego nie było w cieniowania tylko tekstur. Bila nadal ma jednak nieco bezwyrazowy wygląd.  
  
 Prawdziwa kula bilardowa ma zwykle błyszczące wykończenie, które odbija część padającego na światła. Niektóre odzwierciedlone powoduje światła odbitego, które naśladują właściwości odbijające powierzchni. W zależności od właściwości wykończenia refleksy mogą być zlokalizowane lub szerokie, intensywne lub subtelne. Te widowiskowe odbicia są modelowane przy użyciu relacji między źródłem światła, orientacją powierzchni i położeniem kamery — oznacza to, że podświetlenie jest najbardziej intensywne, gdy orientację powierzchnia odbija źródło światła bezpośrednio do aparat, a mniej intensywne, gdy odbicie jest mniej bezpośrednie.  
  
 Model oświetlenie Phong opiera się na modelu oświetlenia Lamberta do uwzględnienia światła odbitego zgodnie z opisem w poprzednim akapicie. Model Phong oświetlenia można dodać do modułu cieniującego, aby nadać bili symulowane zakończenie, która skutkuje bardziej interesującym wyglądem.  
  
#### <a name="to-add-specular-highlights-to-your-shader"></a>Aby dodać światło odbite do modułu cieniującego  
  
1. Zmodyfikuj cieniowanie tak, aby uwzględniało udział odbicia światła przy użyciu mieszania sumującego. Wykres modułu cieniującego powinien wyglądać następująco:  
  
    ![Wykres modułu cieniującego za pomocą odblasków oświetlenia dodano](../designers/media/gfx-shader-demo-billiard-step-3.png "gfx_shader_demo_billiard_step_3")  
  
2. Opcjonalnie można dostosować sposób, który odblasków zachowuje się przez skonfigurowanie właściwości odblasków (**MaterialSpecular** i **MaterialSpecularPower**) modułu cieniującego. Do dostępu do właściwości wykresu cieniowanego, wybierz pusty obszar powierzchni projektu, a następnie w **właściwości** okna, zlokalizuj właściwość, której chcesz uzyskać dostęp.  
  
   Aby uzyskać więcej informacji na temat sposobu stosowania światła odbitego w cieniowaniu, zobacz [jak: Tworzenie podstawowego modułu cieniowanie Phong](../designers/how-to-create-a-basic-phong-shader.md).  
  
   Wyróżnieniem odblasków zastosowane, oświetlenia zwierciadlanego Bila powinna wyglądać mniej więcej tak:  
  
   ![Dodano zbliżenie kuli bilardowej przy użyciu odblasków](../designers/media/gfx-shader-demo-billiard-ball-3.png "gfx_shader_demo_billiard_ball_3")  
  
## <a name="creating-a-sense-of-space-by-reflecting-the-environment"></a>Tworzenie poczucie przestrzeni przez odzwierciedlenie otoczenia  
 Przy użyciu światła odbitego stosowane oświetlenia zwierciadlanego Bila wygląda dość przekonująco. Otrzymano właściwy kształt, wykończenie, kolor i. Istnieje jednak jeszcze jedna technika, która spowoduje, że kula bilardowa wyglądała bardziej jak część jego środowiska.  
  
 Podczas badania prawdziwa kula bilardowa ściśle widać, że jej błyszcząca powierzchnia nie tylko pokazuje odbite światło, ale również lekko odzwierciedla świat wokół niej. Można zasymulować odbicie, używając obrazu środowiska jako tekstury i łącząc go z własną teksturą modelu, aby określić kolor końcowy każdego piksela. W zależności od rodzaju żądanego zakończenia można połączyć więcej lub mniej odbijającej tekstury z resztą cieniowania. Na przykład cieniowanie, które symuluje wysoce odblaskową powierzchnię taką jak może użyć tylko tekstury odbicia, ale cieniowanie, które symuluje bardziej subtelne refleksy, takie jak Lustro na kuli bilardowej, może łączyć tylko niewielki fragment wartości odbicia wartość tekstury z resztą cieniowania obliczenia.  
  
 Oczywiście nie można po prostu zastosować odbitego obrazu do modelu w taki sam sposób stosowania modelu mapę tekstury modelu. Jeśli tak zrobiono, odbicie świat się przemieszczać razem z kuli bilardowej tak, jakby przyklejone do niego. Ponieważ odbicie może pochodzić z dowolnego kierunku, konieczne jest sposób zapewnienia wartości mapy odbić dla każdego kąta i sposób zachowania mapy odbić w orientacji według na świecie. Aby spełnić te wymagania, można użyć specjalnego rodzaju mapy tekstury — o nazwie *mapy modułu*, która zapewnia sześć tekstur rozmieszczonych w formie boków modułu. Z wewnątrz tego modułu można wskazać w dowolnym kierunku, aby znaleźć wartość tekstury. Jeśli tekstury na każdej stronie modułu zawierają obrazy środowiska, można symulować wszelkie odbicia przez próbkowanie poprawnej lokalizacji na powierzchni modułu. Utrzymując dopasowanie modułu do rzeczywistości, uzyskasz dokładne odzwierciedlenie otoczenia. Aby określić, gdzie próbkowania modułu, wystarczy obliczyć tylko odbicie wektora aparatu od powierzchni obiektu, a następnie użyj go jako współrzędne tekstury 3-D. Używanie map modułu w ten sposób jest to typowa technika, który jest znany jako *mapowanie środowiska*.  
  
 Mapowanie środowiska zapewnia efektywne przybliżenie rzeczywistych odbić, zgodnie z opisem w poprzednich akapitach. Odbicia mapowane w środowisku można mieszać w module cieniującym, aby nadać bili symulowane zakończenie, która sprawia, że Bila wydają się więcej na zaangażowaniu w scenie.  
  
 Pierwszym krokiem jest, aby utworzyć tekstury mapy sześcianu. W wielu rodzajach aplikacji zawartość mapy modułu, nie trzeba być idealna działała, szczególnie gdy odbicie jest subtelne lub nie zajmuje ważnego miejsca na ekranie. Na przykład wiele gier używa wstępnie obliczonych map modułów do mapowania środowiska i używa tylko jednej znajdujący się najbliżej każdego obiektu odbijającego światło, mimo że oznacza to, że odbicie nie jest prawidłowy. Nawet zgrubne przybliżenie często jest wystarczająco dobre do przekonującego efektu.  
  
#### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Aby utworzyć tekstury dla mapy środowiska przy użyciu edytora obrazów  
  
1. Utwórz teksturę do pracy. Aby uzyskać informacje dotyczące sposobu dodawania tekstury do projektu, zobacz sekcję pierwsze kroki w [edytora obrazów](../designers/image-editor.md).  
  
2. Ustaw wielkość obrazu tak, aby jej szerokość jest równa jego wysokości i była potęgą liczby dwa; jest to konieczne ze względu na sposób, że mapa sześcienna jest indeksowana. Aby zmienić rozmiar obrazu, w **właściwości** okna, określ nowe wartości **szerokość** i **wysokość** właściwości. Na przykład, ustaw wartość **szerokość** i **wysokość** właściwości do 256.  
  
3. Użyj jednolitego koloru, aby wypełnić teksturę. Tekstura ta będzie dołem mapy modułu, który odpowiada powierzchni stołu bilardowego. Należy pamiętać użyty kolor dla następnej tekstury.  
  
4. Utwórz drugą teksturę, która ma taki sam rozmiar jak pierwsza. Ta Tekstura zostanie powtórzona na czterech bokach mapy modułu, które odnoszą się do powierzchni i bokom stołu bilardowego oraz do obszaru wokół stołu bilardowego. Pamiętaj narysować powierzchnię stołu bilardowego w tej teksturze przy użyciu tego samego koloru, jak Tekstura dolnej. Tekstura powinna wyglądać mniej więcej tak:  
  
    ![Tekstury na boki mapy sześciennej](../designers/media/gfx-shader-demo-billiard-art-env-texture-side.png "gfx_shader_demo_billiard_art_env_texture_side")  
  
    Należy pamiętać, że mapa odzwierciedlenia nie musi być realistyczna, aby była skuteczna; na przykład mapa sześcianu, używana do tworzenia obrazów w tym artykule zawiera tylko cztery kieszenie zamiast sześciu.  
  
5. Utwórz trzecią teksturę, która ma taki sam rozmiar jak pozostałe. Tekstura ta będzie górą mapy modułu, która odpowiada sufitowi nad stołem bilardowym. Aby ta część refleksji była bardziej interesujące, można narysować dodatkowe światło, aby wzmocnić oświetlenie zwierciadlane dodane do modułu cieniującego w poprzedniej procedurze. Tekstura powinna wyglądać mniej więcej tak:  
  
    ![Tekstury do górnej części mapy sześciennej](../designers/media/gfx-shader-demo-billiard-art-env-texture-top2.png "gfx_shader_demo_billiard_art_env_texture_top2")  
  
   Teraz, gdy utworzono poszczególne tekstury na boki mapy modułu, można użyć narzędzia, aby połączyć je w mapę modułu, które mogą być przechowywane w pojedynczym pliku tekstury .dds. Można użyć dowolnego programu, aby utworzyć mapę sześcianu tak długo, jak jego zapisanie mapy sześcianu w formacie tekstury .dds. W tym instruktażu pokazano, jak utworzyć teksturę za pomocą narzędzia DirectX Texture, który jest częścią czerwca 2010 zestawu SDK programu DirectX.  
  
#### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Aby zestawić mapę modułu za pomocą narzędzia DirectX Texture  
  
1. W narzędziu DirectX Texture w menu głównym wybierz **pliku**, **nowa Tekstura**. **Nowa Tekstura** pojawi się okno dialogowe.  
  
2. W **typ tekstury** grupy, wybierz **Tekstura mapy modułu**.  
  
3. W **wymiary** grupy, wprowadź prawidłową wartość **szerokość** i **wysokość**, a następnie wybierz **OK**. Pojawi się nowy dokument tekstury. Domyślnie Tekstura najpierw pokazana w dokumencie tekstur odpowiada **dodatnie X** powierzchni modułu.  
  
4. Załaduj teksturę utworzoną dla boku części modułu tekstury do powierzchni. W menu głównym wybierz **pliku**, **Otwórz na tej powierzchni**, wybierz teksturę utworzoną dla boku modułu, a następnie wybierz **Otwórz**.  
  
5. Powtórz krok 4 dla **ujemne X**, **pozytywne Z**, i **negatywne Z** powierzchni sześcianu. Aby to zrobić, należy wyświetlić twarz, którą chcesz załadować. Aby wyświetlić inną twarz mapy modułu, w menu głównym, wybierz **widoku**, **twarz mapy modułu**, a następnie wybierz twarz, którą chcesz wyświetlić.  
  
6. Aby uzyskać **dodatnie Y** powierzchni modułu, załaduj teksturę utworzoną dla górnej części modułu tekstury.  
  
7. Aby uzyskać **ujemne Y** powierzchni modułu, załaduj teksturę utworzoną dla dolnej części modułu tekstury.  
  
8. Zapisz teksture.  
  
   Można sobie wyobrazić układ mapy modułu następująco:  
  
   ![Układ mapy modułu środowiska](../designers/media/gfx-shader-demo-billiard-art-env-texture-top.png "gfx_shader_demo_billiard_art_env_texture_top")  
  
   Obraz u góry to dodatnia Ściana sześcianu Y (+ Y); w środku od lewej do prawej jest – X + Z, + X i – Z modułu twarzy; u dołu znajduje się ściana sześcianu – Y.  
  
   Teraz można zmodyfikować cieniowanie tak, aby łączyć się próbkę mapy modułu z pozostałą częścią cieniowania.  
  
#### <a name="to-add-environment-mapping-to-your-shader"></a>Aby dodać mapowanie środowiska do modułu cieniującego  
  
1. Zmodyfikuj cieniowanie tak, aby uwzględniało mapowania środowiska przy użyciu mieszania sumującego. Wykres modułu cieniującego powinien wyglądać następująco:  
  
    ![Zbliżenie zarówno rodzaj węzłów cieniowania odbijającą](../designers/media/gfx-shader-demo-billiard-step-4b.png "gfx_shader_demo_billiard_step_4b")  
  
    Należy zauważyć, że można użyć **mnożenie-Dodawanie** węzła w celu uproszczenia wykresu cieniowania.  
  
    Poniżej przedstawiono bardziej szczegółowy widok węzłów cieniowania implementujących mapowanie środowiska:  
  
    ![Wykres modułu cieniującego za pomocą mapowania środowiska dodawane](../designers/media/gfx-shader-demo-billiard-step-4a.png "gfx_shader_demo_billiard_step_4a")  
  
2. Zastosuj teksturę utworzoną w poprzedniej procedurze przez skonfigurowanie właściwości tekstury mapy modułu. Ustaw wartość **tekstury** właściwość **Przykładowa mapa sześcienna** węzeł **Texture2**, a następnie określ plik tekstury za pomocą **Filename**właściwość **Texture2** grupy właściwości.  
  
3. Opcjonalnie można dostosować współczynnik odbicia kuli bilardowej, konfigurując **dane wyjściowe** właściwość **stałej** węzła. Przejdź do właściwości węzła, należy wybrać a następnie w polu **właściwości** okna, zlokalizuj właściwość, której chcesz uzyskać dostęp.  
  
   Za pomocą zastosowania mapowania środowiska Bila powinna wyglądać mniej więcej tak:  
  
   ![Zbliżenie środowiska mapowane kuli bilardowej](../designers/media/gfx-shader-demo-billiard-ball-4.png "gfx_shader_demo_billiard_ball_4")  
  
   W tym obrazie końcowym Zwróć uwagę, jak efektów dodanych łączą się do tworzenia bardzo przekonującą kulę bilardową. Kształt, Tekstura i oświetlenie tworzą podstawowy wygląd obiektu 3-D i światłem odbitym i odbić wprowadzić bili bardziej interesujące i wygląda jak część jego środowiska.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)   
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Edytor obrazów](../designers/image-editor.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
