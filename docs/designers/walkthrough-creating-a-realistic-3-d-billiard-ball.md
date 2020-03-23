---
title: 'Instruktaż: Tworzenie realistycznej kuli bilardowej 3D'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 866f91303c224f8330a4d2be76f3d29331fcb346
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589919"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Przewodnik: tworzenie realistycznej kuli bilardowej w 3D

W tym przewodniku pokazano, jak utworzyć realistyczną kulę bilardową 3D przy użyciu projektanta cieniowania i edytora obrazów w programie Visual Studio. Wygląd 3D kuli bilardowej uzyskuje się poprzez połączenie kilku technik cieniowania z odpowiednimi zasobami tekstury.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebne są następujące składniki i umiejętności:

- Narzędzie do składania tekstur w mapie modułu, takie jak narzędzie DirectX Texture Tool zawarte w zestawie SDK DirectX z czerwca 2010.

- Znajomość edytora obrazów w programie Visual Studio.

- Znajomość projektanta modułu cieniującego w programie Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Tworzenie podstawowego wyglądu z kształtem i teksturą

W grafice komputerowej najbardziej podstawowymi elementami wyglądu są kształt i kolor. W symulacji komputerowej często używa się modelu 3D do reprezentowania kształtu obiektu w świecie rzeczywistym. Szczegóły kolorów są następnie stosowane do powierzchni modelu przy użyciu mapy tekstury.

Zazwyczaj może być trzeba poprosić wykonawcę, aby utworzyć model 3D, który można użyć, ale ponieważ kula bilardowa jest wspólny kształt (kula), Projektant modułu cieniującego ma już odpowiedni model wbudowany.

Kula jest domyślnym kształtem podglądu w Projektancie modułu cieniującego; Jeśli do podglądu modułu cieniującego jest obecnie używany inny kształt, przełącz się z powrotem do kuli.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Aby wyświetlić podgląd modułu cieniującego przy użyciu kuli

- Na pasku narzędzi Projektanta modułów cieniucych wybierz pozycję **Podgląd ze sferą.**

W następnym kroku utworzysz program do cieniowania, który zastosuje teksturę do modelu, ale najpierw musisz utworzyć teksturę, której można użyć. W tym przewodniku pokazano, jak utworzyć teksturę za pomocą Edytora obrazów, który jest częścią programu Visual Studio, ale można użyć dowolnego edytora obrazów, który można zapisać tekstury w odpowiednim formacie.

Upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Aby utworzyć teksturę kuli bilardowej za pomocą Edytora obrazów

1. Utwórz teksturę do pracy. Aby uzyskać informacje dotyczące dodawania tekstury do projektu, zobacz sekcję Wprowadzenie w [Edytorze obrazów](../designers/image-editor.md).

2. Ustaw rozmiar obrazu tak, aby jego szerokość była dwukrotnie większa; jest to konieczne ze względu na sposób, w jaki tekstura jest odwzorowana na kulistej powierzchni kuli bilardowej. Aby zmienić rozmiar obrazu, w oknie **Właściwości** określ nowe wartości właściwości **Szerokość** i **Wysokość.** Na przykład ustaw szerokość 512 i wysokość na 256.

3. Narysuj teksturę kuli bilardowej, pamiętając o tym, jak tekstura jest odwzorowana na kuli.

    Tekstura powinna wyglądać podobnie do tego:

    ![Tekstura kuli bilardowej](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. Opcjonalnie można zmniejszyć wymagania dotyczące magazynowania tej tekstury. Można to zrobić, zmniejszając szerokość tekstury, aby dopasować jej wysokość. To kompresuje teksturę wzdłuż jego szerokości, ale ze względu na sposób, w jaki tekstura jest odwzorowana na kulę, zostanie ona rozszerzona, gdy kula bilardowa zostanie renderowana. Po zmisowaniu tekstura powinna wyglądać podobnie do tej:

    ![Tekstura bilardowa skompresowana do kwadratu](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Teraz można utworzyć moduł cieniujący, który stosuje tę teksturę do modelu.

### <a name="to-create-a-basic-texture-shader"></a>Aby utworzyć podstawowy moduł cieniujący tekstury

1. Utwórz moduł cieniujący DGSL, z którym ma być działać. Aby uzyskać informacje dotyczące dodawania modułu cieniującego DGSL do projektu, zobacz sekcję Wprowadzenie w [Projektancie modułu cieniującego](../designers/shader-designer.md).

    Domyślnie wykres modułu cieniującego wygląda następująco:

    ![Domyślny wykres modułu cieniującego](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Zmodyfikuj domyślny moduł cieniujący, tak aby stos był wartość próbki tekstury do bieżącego piksela. Wykres modułu cieniującego powinien wyglądać następująco:

    ![Wykres modułu cieniującego, który stosuje teksturę do obiektu](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Zastosuj teksturę utworzoną w poprzedniej procedurze, konfigurując właściwości tekstury. Ustaw wartość **właściwości Texture węzła** **Texture sample** na **Texture1,** a następnie określ plik tekstury za pomocą właściwości **Nazwa pliku** grupy właściwości **Texture1** w tym samym oknie właściwości.

   Aby uzyskać więcej informacji na temat stosowania tekstury w modułie cieniującym, zobacz [Jak: Tworzenie podstawowego modułu cieniującego tekstury](../designers/how-to-create-a-basic-texture-shader.md).

   Twoja kula bilardowa powinna teraz wyglądać podobnie do tej:

   ![Zbliżenie teksturowanej kuli bilardowej](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Tworzenie głębi dzięki modelowi oświetlenia Lambert

Do tej pory stworzyłeś łatwo rozpoznawalną kulę bilardową. Wydaje się jednak płaska i nieciekawa – bardziej przypomina kreskówkowy obraz kuli bilardowej niż przekonującą replikę. Płaski wygląd wynika z uproszczonego modułu cieniującego, który zachowuje się tak, jakby każdy piksel na powierzchni kuli bilardowej otrzymywał taką samą ilość światła.

W świecie rzeczywistym światło wydaje się najjaśniejsze na powierzchniach, które bezpośrednio wychodzą na źródło światła i wydaje się mniej jasne na powierzchniach, które znajdują się pod kątem ukośnym do źródła światła. Dzieje się tak dlatego, że energia w promieniach światła jest rozprowadzana na najmniejszej powierzchni, gdy powierzchnia bezpośrednio wychodzi na światło. Gdy powierzchnia odwraca się od źródła światła, ta sama ilość energii jest rozprowadzana na coraz większej powierzchni. Powierzchnia, która jest skierowana z dala od źródła światła, nie otrzymuje energii świetlnej, co powoduje całkowicie ciemny wygląd. Ta wariancja jasności na powierzchni obiektu jest ważnym sygnałem wizualnym, który pomaga wskazać kształt obiektu; bez niego obiekt wydaje się płaski.

W grafice komputerowej *modele oświetlenia*— uproszczone przybliżenia złożonych, rzeczywistych interakcji oświetlenia — służą do replikowania wyglądu oświetlenia w świecie rzeczywistym. Model oświetlenia Lamberta zmienia ilość rozproszonego światła odbitego na powierzchni obiektu, jak opisano w poprzednim akapicie. Możesz dodać model oświetlenia Lamberta do modułu cieniującego, aby nadać kuli bilardowej bardziej przekonujący wygląd 3D.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Aby dodać oświetlenie Lamberta do modułu cieniującego

- Zmodyfikuj moduł cieniujący, aby modulować wartość próbki tekstury według wartości oświetlenia Lambert. Wykres modułu cieniującego powinien wyglądać następująco:

   ![Dodano wykres modułu cieniującego z oświetleniem Lambert](../designers/media/gfx_shader_demo_billiard_step_2.png)

- Opcjonalnie można dostosować zachowanie oświetlenia, konfigurując **właściwość MaterialDiffuse** wykresu modułu cieniującego. Aby uzyskać dostęp do właściwości wykresu modułu cieniującego, wybierz pusty obszar powierzchni projektowej, a następnie zlokalizuj właściwość, do której chcesz uzyskać dostęp w oknie **Właściwości.**

Aby uzyskać więcej informacji na temat stosowania oświetlenia Lambert w modułie cieniującym, zobacz [Jak: Tworzenie podstawowego modułu cieniującego Lambert](../designers/how-to-create-a-basic-lambert-shader.md).

Po zastosowanym oświetleniu Lamberta kula bilardowa powinna wyglądać podobnie do tej:

![Zbliżenie teksturowanej i oświetlonej kuli bilardowej](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Popraw podstawowy wygląd dzięki specular highlights

Model oświetlenia Lambert zapewnia poczucie kształtu i wymiaru, który był nieobecny w shaderze tylko do tekstury. Jednak piłka bilardowa nadal ma nieco nudny wygląd.

Prawdziwa kula bilardowa ma zwykle błyszczące wykończenie, które odzwierciedla część światła, które na nią spada. Niektóre z tych odbitych wyników światła w światłach lustrzanych, które symulują właściwości odbijające powierzchnię. W zależności od właściwości wykończenia, światła mogą być zlokalizowane lub szerokie, intensywne lub subtelne. Te odbicia lustrzane są modelowane przy użyciu relacji między źródłem światła, orientacją powierzchni i położeniem kamery , to jest, że podświetlenie jest najbardziej intensywne, gdy orientacja powierzchni odbija źródło światła bezpośrednio do i jest mniej intensywny, gdy odbicie jest mniej bezpośrednie.

Model oświetlenia Phong opiera się na modelu oświetlenia Lambert, aby uwzględnić światła lustrzane, jak opisano w poprzednim akapicie. Możesz dodać model oświetlenia Phong do modułu cieniującego, aby nadać kuli bilardowej symulowane wykończenie, które powoduje bardziej interesujący wygląd.

### <a name="to-add-specular-highlights-to-your-shader"></a>Aby dodać światła lustrzane do modułu cieniującego

1. Zmodyfikuj moduł cieniujący, aby uwzględnić wkład lustrzany przy użyciu mieszania dodatków. Wykres modułu cieniującego powinien wyglądać następująco:

    ![Dodano wykres modułu cieniującego z oświetleniem lustrzanym](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. Opcjonalnie można dostosować sposób zachowania podświetlenia lustrzanego, konfigurując właściwości lustrzane **(MaterialSpecular** i **MaterialSpecularPower)** wykresu modułu cieniującego. Aby uzyskać dostęp do właściwości wykresu modułu cieniującego, wybierz pusty obszar powierzchni projektowej, a następnie w oknie **Właściwości** znajdź właściwość, do której chcesz uzyskać dostęp.

   Aby uzyskać więcej informacji na temat stosowania świateł lustrzanych w modułie cieniującym, zobacz [Jak: Tworzenie podstawowego modułu cieniującego Phong](../designers/how-to-create-a-basic-phong-shader.md).

   Z specular highlighting stosowane, twoja kula bilardowa powinna wyglądać podobnie do tego:

   ![Zbliżenie kuli bilardowej z dodanym odwzórem](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Tworzenie poczucia przestrzeni poprzez odzwierciedlenie środowiska

Z specular podkreśla stosowane, piłka bilard wygląda dość przekonujące. Ma odpowiedni kształt, właściwą pracę lakierniczą i właściwe wykończenie. Jednak jest jeszcze jedna technika, która sprawi, że twoja kula bilardowa będzie wyglądać bardziej jak część jej środowiska.

Jeśli dokładnie zbadasz prawdziwą kulę bilardową, zobaczysz, że jej błyszcząca powierzchnia nie tylko wykazuje specular highlights, ale także słabo odzwierciedla obraz świata wokół niego. Odbicie można symulować, używając obrazu środowiska jako tekstury i łącząc je z własną teksturą modelu, aby określić ostateczny kolor każdego piksela. W zależności od rodzaju wykończenia można połączyć mniej więcej tekstury odbicia z resztą modułu cieniującego. Na przykład moduł cieniujący, który symuluje wysoce odblaskową powierzchnię, taką jak lustro, może używać tylko tekstury odbicia, ale moduł cieniujący, który symuluje bardziej subtelne odbicie, takie jak ten znaleziony na kuli bilardowej, może łączyć tylko niewielką część odbicia wartości tekstury wraz z resztą obliczeń modułu cieniującego.

Oczywiście nie można po prostu zastosować odbitego obrazu do modelu w taki sam sposób, w jaki zastosujesz mapę tekstur modelu. Gdybyś tak było, odbicie świata poruszałoby się z kulą bilardową, jakby odbicie było do niej przyklejone. Ponieważ odbicie może pochodzić z dowolnego kierunku, potrzebujesz sposobu, aby zapewnić wartość mapy odbicia dla dowolnego kąta, i sposobu, aby mapa odbicia była zorientowana zgodnie ze światem. Aby spełnić te wymagania, można użyć specjalnego rodzaju mapy tekstur , zwanego *mapą modułu,* która zawiera sześć tekstur ułożonych w celu utworzenia boków modułu. Od wewnątrz tego modułu można wskazać w dowolnym kierunku, aby znaleźć wartość tekstury. Jeśli tekstury po obu stronach modułu zawierają obrazy środowiska, można symulować każde odbicie, pobierając próbki poprawnej lokalizacji na powierzchni modułu. Utrzymując kostkę dostosowaną do świata, otrzymasz dokładne odbicie środowiska. Aby określić, gdzie moduł ma być próbkowany, wystarczy obliczyć odbicie wektora kamery z powierzchni obiektu, a następnie użyć go jako współrzędne tekstury 3D. Korzystanie z map sześcianu w ten sposób jest powszechną techniką, która jest znana jako *mapowanie środowiska*.

Mapowanie środowiska zapewnia efektywne przybliżenie rzeczywistych odbić, zgodnie z opisem w poprzednich akapitach. Możesz połączyć odbicia odwzorowane w środowisku do modułu cieniującego, aby nadać kuli bilardowej symulowane wykończenie, które sprawia, że kula bilardowa wydaje się bardziej uziemiona na scenie.

Pierwszym krokiem jest utworzenie tekstury mapy modułu. W wielu rodzajach aplikacji zawartość mapy modułu nie musi być idealna, aby była skuteczna, zwłaszcza gdy odbicie jest subtelne lub nie zajmuje znaczącej przestrzeni na ekranie. Na przykład wiele gier używa wstępnie obliczonych map modułu do mapowania środowiska i po prostu używa najbliższego każdemu obiektowi odblaskowego, chociaż oznacza to, że odbicie nie jest poprawne. Nawet przybliżone przybliżenie jest często wystarczająco dobre, aby uzyskać przekonujący efekt.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Aby utworzyć tekstury dla mapy środowiska za pomocą Edytora obrazów

1. Utwórz teksturę do pracy. Aby uzyskać informacje dotyczące dodawania tekstury do projektu, zobacz sekcję Wprowadzenie w [Edytorze obrazów](../designers/image-editor.md).

2. Ustaw rozmiar obrazu tak, aby jego szerokość była równa jego wysokości i jest potęgą o rozmiarze dwóch; jest to konieczne ze względu na sposób indeksowania mapy modułu. Aby zmienić rozmiar obrazu, w oknie **Właściwości** określ nowe wartości właściwości **Szerokość** i **Wysokość.** Na przykład ustaw wartość **width** i **height** właściwości 256.

3. Użyj jednolitego koloru, aby wypełnić teksturę. Ta tekstura będzie dolną częścią mapy sześcianu, co odpowiada powierzchni stołu bilardowego. Pamiętaj o kolorze użytym w przypadku następnej tekstury.

4. Utwórz drugą teksturę o tym samym rozmiarze co pierwsza. Tekstura ta zostanie powtórzona po czterech stronach mapy sześcianu, które odpowiadają powierzchni i bokom stołu bilardowego oraz obszarowi wokół stołu bilardowego. Pamiętaj, aby narysować powierzchnię stołu bilardowego w tej teksturze przy użyciu tego samego koloru, co w dolnej teksturze. Tekstura powinna wyglądać podobnie do tego:

    ![Tekstura boków mapy kostki](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Pamiętaj, że mapa refleksji nie musi być fotorealistyczna, aby była skuteczna; na przykład mapa modułu użyta do utworzenia obrazów w tym artykule zawiera tylko cztery kieszenie zamiast sześciu.

5. Utwórz trzecią teksturę o tym samym rozmiarze co pozostałe. Ta tekstura będzie górna część mapy kostki, która odpowiada sufitowi nad stołem bilardowym. Aby ta część odbicia była bardziej interesująca, można narysować światło napowietrzne, aby wzmocnić światła lustrzane dodane do modułu cieniującego w poprzedniej procedurze. Tekstura powinna wyglądać podobnie do tego:

    ![Tekstura górnej części mapy kostki](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Po utworzeniu poszczególnych tekstur dla boków mapy modułu można użyć narzędzia do zmontowania ich w mapę modułu, która może być przechowywana w pojedynczej teksturze *.dds.* Możesz użyć dowolnego programu, który ma zostać utworzony na mapie modułu, o ile może zapisać mapę modułu w formacie tekstury .dds. W tym przewodniku pokazano, jak utworzyć teksturę przy użyciu narzędzia DirectX Texture Tool, które jest częścią zestawu SDK DirectX z czerwca 2010 r.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Aby zmontować mapę sześcianu za pomocą narzędzia Tekstura DirectX

1. W narzędziu DirectX Texture Tool w menu głównym wybierz polecenie **Plik** > **nowa tekstura**. Zostanie wyświetlone okno dialogowe **Nowa tekstura.**

2. W grupie **Typ tekstury** wybierz pozycję **Tekstura mapy modułu**.

3. W grupie **Wymiary** wprowadź prawidłową wartość **szerokości** i **wysokości,** a następnie wybierz przycisk **OK**. Zostanie wyświetlony nowy dokument tekstury. Domyślnie tekstura po raz pierwszy pokazana w dokumencie tekstury odpowiada powierzchni modułu **Dodatnia X.**

4. Załaduj utworzoną teksturę z boku sześcianu tekstury na ścianę sześcianu. W menu głównym wybierz polecenie **Otwórz plik** > **na tej ścianie mapy kostek**, wybierz teksturę utworzoną dla boku modułu, a następnie wybierz pozycję **Otwórz**.

5. Powtórz krok 4 dla **ścian ujemnych X,** **dodatnich Z**i **ujemnych Z.** Aby to zrobić, należy wyświetlić twarz, którą chcesz załadować. Aby wyświetlić inną ścianę mapy modułu, w menu głównym wybierz polecenie **Wyświetl** > **ścianę mapy kostki,** a następnie wybierz ścianę, którą chcesz wyświetlić.

6. W przypadku ściany modułu **Dodatnia wartość Y** załaduj teksturę utworzoną dla górnej części modułu tekstury.

7. W przypadku ściany modułu **Ujemna Y** załaduj teksturę utworzoną na dole modułu tekstury.

8. Zapisz teksturę.

   Możesz sobie wyobrazić układ mapy modułu w ten sposób:

   ![Układ mapy modułu środowiska](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Obraz u góry jest dodatnią twarzą sześcianu Y (+Y); w środku, od lewej do prawej, jest -X, +Z, +X i -Z ściany sześcianu; na dole znajduje się ściana kostki -Y.

   Teraz można zmodyfikować moduł cieniujący, aby wymieszać próbkę mapy modułu z resztą modułu cieniującego.

### <a name="to-add-environment-mapping-to-your-shader"></a>Aby dodać mapowanie środowiska do modułu cieniującego

1. Zmodyfikuj moduł cieniujący, aby uwzględnić wkład mapowania środowiska przy użyciu mieszania dodatków. Wykres modułu cieniującego powinien wyglądać następująco:

    ![Zbliżenie obu rodzajów węzłów odblaskowych modułów cieniowania](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Należy zauważyć, że można użyć **węzła Multiply-Add,** aby uprościć wykres modułu cieniującego.

    Oto bardziej szczegółowy widok węzłów modułu cieniującego, które implementują mapowanie środowiska:

    ![Wykres modułu cieniującego z dodanym mapowaniem środowiska](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Zastosuj teksturę utworzoną w poprzedniej procedurze, konfigurując właściwości tekstury mapy modułu. Ustaw wartość **właściwości Texture** węzła Sample mapy **modułu** na **Texture2,** a następnie określ plik tekstury za pomocą właściwości **Nazwa pliku** grupy właściwości **Texture2.**

3. Opcjonalnie można dostosować współczynnik odbicia kuli bilardowej, konfigurując właściwość **Output** węzła **Stała.** Aby uzyskać dostęp do właściwości węzła, zaznacz go, a następnie w oknie **Właściwości,** znajdź właściwość, do której chcesz uzyskać dostęp.

   Po zastosowaniu mapowania środowiska kula bilardowa powinna wyglądać podobnie do:

   ![Zbliżenie środowiska odwzorowane kula bilardowa](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   Na tym ostatnim obrazie zwróć uwagę na to, jak dodane efekty łączą się, aby stworzyć bardzo przekonującą kulę bilardową. Kształt, tekstura i oświetlenie tworzą podstawowy wygląd obiektu 3D, a lustrzane światła i odbicia sprawiają, że kula bilardowa jest bardziej interesująca i wygląda jak część otoczenia.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
