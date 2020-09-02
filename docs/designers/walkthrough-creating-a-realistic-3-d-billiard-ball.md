---
title: 'Przewodnik: tworzenie realistycznej kulki 3W bilardowej'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bebaa8c197d0b0a4447739d900062bef2bda37c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816660"
---
# <a name="walkthrough-create-a-realistic-3d-billiard-ball"></a>Przewodnik: Tworzenie realistycznej kuli bilardowej w 3D

W tym instruktażu pokazano, jak utworzyć realistyczną kulkę bilardowej 3W przy użyciu projektanta programu do cieniowania i edytora obrazów w programie Visual Studio. Wygląd 3D kulki bilardowej jest osiągany przez połączenie kilku technik cieniowania z odpowiednimi zasobami tekstury.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebne są następujące składniki i umiejętności:

- Narzędzie do składania tekstur do mapy modułu, na przykład narzędzie DirectX Texture, które jest zawarte w zestawie SDK DirectX 2010 dla czerwca.

- Znajomość edytora obrazów w programie Visual Studio.

- Znajomość projektanta programu do cieniowania w programie Visual Studio.

## <a name="create-the-basic-appearance-with-shape-and-texture"></a>Tworzenie podstawowego wyglądu przy użyciu kształtu i tekstury

W grafikach komputerowych najbardziej podstawowe elementy wyglądu są kształtem i kolorem. W symulacji komputera często należy używać modelu 3D do reprezentowania kształtu rzeczywistego obiektu. Szczegóły koloru są następnie stosowane do powierzchni modelu przy użyciu mapy tekstury.

Zwykle może zaistnieć konieczność poproszenia wykonawcy o utworzenie modelu 3D, którego można użyć, ale ponieważ bilardowej piłka jest wspólnym kształtem (sferą), Projektant cieniowania ma już wbudowany odpowiedni model.

Sfera jest domyślnym kształtem podglądu w projektancie cieniowania; Jeśli obecnie używasz innego kształtu do podglądu cieniowania, przełącz się z powrotem do sfery.

### <a name="to-preview-the-shader-by-using-a-sphere"></a>Aby wyświetlić podgląd cieniowania przy użyciu sfery

- Na pasku narzędzi projektanta cieniowania wybierz pozycję **Podgląd z sferą.**

W następnym kroku utworzysz program do cieniowania, który stosuje teksturę do modelu, ale najpierw musisz utworzyć teksturę, której można użyć. W tym instruktażu przedstawiono sposób tworzenia tekstury przy użyciu edytora obrazów, który jest częścią programu Visual Studio, ale można użyć dowolnego edytora obrazów, który umożliwia zapisanie tekstury w odpowiednim formacie.

Upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Aby utworzyć teksturę bilardowej kulki przy użyciu edytora obrazów

1. Utwórz teksturę, z którą chcesz współpracować. Aby uzyskać informacje na temat sposobu dodawania tekstury do projektu, zobacz sekcję Wprowadzenie w [Edytorze obrazu](../designers/image-editor.md).

2. Ustaw rozmiar obrazu tak, aby jego szerokość była dwukrotnie równa wysokości; jest to konieczne ze względu na sposób, w jaki tekstura jest mapowana na sferyczną powierzchnię kulki bilardowej. Aby zmienić rozmiar obrazu, w oknie **Właściwości** Określ nowe wartości właściwości **Width** i **Height** . Na przykład Ustaw szerokość na 512 i wysokość na 256.

3. Narysuj teksturę dla kulki bilardowej, pamiętając o tym, jak tekstura jest mapowana na sferę.

    Tekstura powinna wyglądać podobnie do tego:

    ![Tekstura kulki bilardowej](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png)

4. Opcjonalnie możesz chcieć zmniejszyć wymagania dotyczące magazynu tej tekstury. Można to zrobić, zmniejszając szerokość tekstury w celu dopasowania jej do wysokości. Kompresuje teksturę wzdłuż jej szerokości, ale ze względu na sposób, w jaki tekstura jest mapowana do sfery, zostanie rozwinięta, gdy kulka bilardowej jest renderowana. Po zmianie wielkości tekstura powinna wyglądać podobnie do tego:

    ![Tekstura bilardowej została skompresowana do kwadratu](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png)

   Teraz można utworzyć cieniowanie, które stosuje tę teksturę do modelu.

### <a name="to-create-a-basic-texture-shader"></a>Aby utworzyć cieniowanie tekstury podstawowej

1. Utwórz program do cieniowania DGSL, który będzie działał. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

    Domyślnie wykres programu do cieniowania wygląda następująco:

    ![Domyślny wykres cieniowania](../designers/media/gfx_shader_demo_billiard_step_0.png)

2. Zmodyfikuj domyślne cieniowanie tak, aby stosowało wartość próbki tekstury do bieżącego piksela. Wykres modułu cieniującego powinien wyglądać następująco:

    ![Wykres programu do cieniowania, który stosuje teksturę do obiektu](../designers/media/gfx_shader_demo_billiard_step_1.png)

3. Zastosuj teksturę utworzoną w poprzedniej procedurze przez skonfigurowanie właściwości tekstury. Ustaw wartość właściwości **tekstura** węzła **przykład tekstury** na **texture1**, a następnie określ plik tekstury przy użyciu właściwości **filename** grupy właściwości **texture1** w tym samym oknie właściwości.

   Aby uzyskać więcej informacji na temat sposobu stosowania tekstury w module cieniującego, zobacz [How to: Create a Basic — cieniowanie tekstury](../designers/how-to-create-a-basic-texture-shader.md).

   Kulka bilardowej powinna teraz wyglądać podobnie do tego:

   ![Closeupa bilardoweja z teksturą](../designers/media/gfx_shader_demo_.png)

## <a name="create-depth-with-the-lambert-lighting-model"></a>Utwórz głębokość przy użyciu modelu oświetlenia Lamberta

Do tej pory utworzono łatwą do rozpoznania kulkę bilardowej. Jednak jest ona płaska i nieinteresująca — podobnie jak w przypadku kreskówkiej kulki bilardowej niż przekonująca replika. Płaski wygląd wynika z cieniowania uproszczony, który zachowuje się tak, jakby każdy piksel na powierzchni kuli bilardowej odbierze tę samą ilość światła.

W świecie rzeczywistym światła pojawiają się najjaśniejsze na powierzchniach bezpośrednio skierowanych do źródła światła i pojawiają się mniej jasne na powierzchniach, które mają kąt skośny względem źródła światła. Wynika to z faktu, że energia w promieniach świetlnych jest dystrybuowana na najmniejszym obszarze powierzchni, gdy powierzchnia jest bezpośrednio skierowana do źródła światła. Gdy powierzchnia zostanie odłożona od źródła światła, taka sama ilość energii jest rozprowadzana na coraz większym obszarze powierzchni. Powierzchnia, która odchodzi od źródła światła, nie otrzymuje żadnej lekkiej energii, co spowodowało całkiem ciemny wygląd. Ta Wariancja w całej powierzchni obiektu jest ważnym wizualnym wskaźnikiem, który pomaga wskazać kształt obiektu; bez niego, obiekt pojawia się płaski.

W przypadku grafiki komputerowej *modele oświetlenia*— uproszczone przybliżenie skomplikowanych interakcji z rzeczywistymi oświetleniem — są używane do replikowania wyglądu rzeczywistych oświetlenia. Model oświetlenia Lamberta zmienia liczbę diffusely odzwierciedlonych przez powierzchnię obiektu, zgodnie z opisem w poprzednim akapicie. Model oświetlenia Lamberta można dodać do modułu cieniującego, aby dać piłkę bilardowej bardziej przekonujący wygląd 3W.

### <a name="to-add-lambert-lighting-to-your-shader"></a>Aby dodać oświetlenie Lamberta do programu do cieniowania

- Zmodyfikuj cieniowanie, aby modulacja wartości próbki tekstury przez wartość oświetlenia Lamberta. Wykres modułu cieniującego powinien wyglądać następująco:

   ![Wykres modułu cieniującego z dodanym oświetleniem Lamberta](../designers/media/gfx_shader_demo_billiard_step_2.png)

- Opcjonalnie można dostosować sposób działania oświetlenia przez skonfigurowanie właściwości **MaterialDiffuse** wykresu cieniowania. Aby uzyskać dostęp do właściwości wykresu cieniowania, wybierz pusty obszar powierzchni projektowej, a następnie zlokalizuj właściwość, do której chcesz uzyskać dostęp w oknie **Właściwości** .

Aby uzyskać więcej informacji na temat sposobu stosowania oświetlenia Lamberta w module cieniującego, zobacz [How to: Create a Basic Lamberta Shader](../designers/how-to-create-a-basic-lambert-shader.md).

Po zastosowaniu oświetlenia Lamberta, kulka bilardowej powinna wyglądać podobnie do tego:

![Closeupa z teksturą i oświetlonyą bilardowej](../designers/media/gfx_shader_demo_billiard_ball_2.png)

## <a name="enhance-the-basic-appearance-with-specular-highlights"></a>Rozszerzanie podstawowego wyglądu z odblaskówymi wyróżnieniami

Model oświetlenia Lamberta zapewnia sensie kształtu i wymiaru, który był nieobecny w cieniowaniu wyłącznie tekstury. Jednak kula bilardowej nadal ma nieco bardziej matowy wygląd.

Rzeczywista piłka bilardowej zazwyczaj ma błyszczące zakończenie, które odzwierciedla część jasnego światła. Niektóre z tych widocznych sygnalizatorów są wyróżnione odblasków, które symulują odbicie właściwości powierzchni. W zależności od właściwości zakończenia światła mogą być lokalizowane lub szerokie, intensywnie lub subtelne. Te odbicia odblasków są modelowane przy użyciu relacji między źródłem światła, orientacją powierzchni i położeniem kamery — to znaczy, że wyróżnienie jest najbardziej intensywne, gdy orientacja powierzchni odzwierciedla źródło światła bezpośrednio do aparatu, i jest mniej intensywna, gdy odbicie jest mniej bezpośrednie.

Model oświetlenia podstawowego Phong jest oparty na modelu oświetlenia Lamberta, aby obejmował odblaskówe, zgodnie z opisem w poprzednim akapicie. Model oświetlenia podstawowego Phong można dodać do programu do cieniowania, aby dać kulkę bilardowej, która daje w wyniku bardziej interesujący wygląd.

### <a name="to-add-specular-highlights-to-your-shader"></a>Aby dodać pododblaskówki do programu do cieniowania

1. Zmodyfikuj cieniowanie tak, aby obejmowało wkład odblasków przy użyciu mieszania dodatków. Wykres modułu cieniującego powinien wyglądać następująco:

    ![Wykres modułu cieniującego z dodanym oświetleniem odblasków](../designers/media/gfx_shader_demo_billiard_step_3.png)

2. Opcjonalnie możesz dostosować sposób, w jaki odblasków wyróżnienia, konfigurując właściwości odblasków (**MaterialSpecular** i **MaterialSpecularPower**) grafu cieniowania. Aby uzyskać dostęp do właściwości wykresu cieniowania, wybierz pusty obszar powierzchni projektowej, a następnie w oknie **Właściwości** Znajdź właściwość, do której chcesz uzyskać dostęp.

   Aby uzyskać więcej informacji na temat sposobu stosowania odblaskówch świateł w module cieniującego, zobacz [How to: Create a Basic podstawowego Phong Shader](../designers/how-to-create-a-basic-phong-shader.md).

   Po zastosowaniu wyróżniania odblasków, kulka bilardowej powinna wyglądać podobnie do tego:

   ![Closeup kulki bilardowej z dodaną odblasków](../designers/media/gfx_shader_demo_billiard_ball_3.png)

## <a name="create-a-sense-of-space-by-reflecting-the-environment"></a>Tworzenie sensu przestrzeni przez odzwierciedlenie środowiska

Po zastosowaniu wyróżnionych odblasków, kulka bilardowej wygląda dość przekonujący. Uzyskano odpowiedni kształt, odpowiednie zadanie malowania i zakończenie. Istnieje jednak jeszcze jedna technika, która sprawia, że kulka bilardowej będzie wyglądała podobnie jak część środowiska.

Jeśli dokładnie sprawdzisz rzeczywistą kulkę z bilardowej, zobaczysz, że jej błyszcząca powierzchnia nie wykazuje odblaskówych świateł, ale również pokazuje obraz wokół niego. Można symulować to odbicie przy użyciu obrazu środowiska jako tekstury i połączyć go z teksturą modelu, aby określić końcowy kolor każdego piksela. W zależności od rodzaju dokończenia możesz łączyć więcej lub mniej tekstury odbicia razem z resztą cieniowania. Na przykład, cieniowanie, które symuluje wysoce odbijającą powierzchnię, taką jak dublowanie, może używać tylko tekstury odbicia, ale cieniowanie, które symuluje bardziej subtelne odbicie, takie jak element znaleziony w piłke bilardowej, może łączyć tylko małą część wartości tekstury odbicia wraz z resztą obliczeń cieniowania.

Oczywiście nie można po prostu zastosować odbitego obrazu do modelu w taki sam sposób, w jaki stosowana jest mapa Tekstury modelu. Jeśli zachodzi taka potrzeba, odbicie świata będzie przenoszone z piłką bilardowej, tak jakby odbicie zostało przyklejony do niego. Ponieważ odbicie może pochodzić z dowolnego kierunku, potrzebny jest sposób zapewnienia wartości mapy odbicia dla dowolnego kąta i sposób zachowania mapy odbicia na całym świecie. Aby spełnić te wymagania, można użyć specjalnego rodzaju mapy tekstury — nazywanej *mapą modułu*, która oferuje sześć tekstur zorganizowanych w celu utworzenia boków modułu. Z wnętrza tego modułu można wskazać w dowolnym kierunku, aby znaleźć wartość tekstury. Jeśli tekstury na każdej stronie modułu zawierają obrazy środowiska, można symulować dowolne odbicie przez próbkowanie właściwej lokalizacji na powierzchni modułu. Utrzymując moduł wyrównany do świata, uzyskasz dokładne odbicie środowiska. Aby określić, gdzie należy próbkować moduł, wystarczy obliczyć odbicie wektora aparatu poza powierzchnią obiektu, a następnie użyć go jako współrzędnej tekstury 3D. Korzystanie z map modułów w ten sposób jest typową techniką nazywaną *mapowaniem środowiska*.

Mapowanie środowiska zapewnia wydajne przybliżenie rzeczywistych odbić, jak opisano w poprzednich akapitach. Możesz mieszać odbicie mapowane w środowisku do modułu cieniującego, aby dać kulkę bilardoweją, która sprawia, że kulka bilardowej jest bardziej uziemiona w scenie.

Pierwszym krokiem jest utworzenie tekstury mapy modułu. W wielu rodzajach aplikacji zawartość mapy modułu nie musi być skuteczna, szczególnie gdy odbicie jest subtelne lub nie zajmuje widocznego miejsca na ekranie. Na przykład w wielu grach użyto wstępnie obliczonych map modułów do mapowania środowiska i po prostu Użyj jednego z najbliższych do każdego obiektu odbicia, chociaż oznacza to, że odbicie nie jest prawidłowe. Nawet przybliżone przybliżenie jest często dobrym rozwiązaniem dla przekonującego efektu.

### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Aby utworzyć tekstury dla mapy środowiska przy użyciu edytora obrazów

1. Utwórz teksturę, z którą chcesz współpracować. Aby uzyskać informacje na temat sposobu dodawania tekstury do projektu, zobacz sekcję Wprowadzenie w [Edytorze obrazu](../designers/image-editor.md).

2. Ustaw rozmiar obrazu tak, aby jego szerokość była równa wysokości i jest potęgą dwóch rozmiarów. jest to konieczne ze względu na sposób, w jaki mapa modułu jest indeksowana. Aby zmienić rozmiar obrazu, w oknie **Właściwości** Określ nowe wartości właściwości **Width** i **Height** . Na przykład ustaw wartość właściwości **Width** i **Height** na 256.

3. Użyj pełnego koloru, aby wypełnić teksturę. Teksturą będzie dolna część mapy modułu, która odnosi się do powierzchni tabeli bilardowej. Zachowaj użyty kolor dla następnej tekstury.

4. Utwórz drugą teksturę, która ma taki sam rozmiar jak pierwsza. Ta tekstura będzie powtarzana na czterech stronach mapy modułu, która odnosi się do powierzchni i boków tabeli bilardowej oraz do obszaru wokół tabeli bilardowej. Pamiętaj, aby narysować powierzchnię tabeli bilardowej w tej tekstury przy użyciu tego samego koloru jak w przypadku tekstury dolnej. Tekstura powinna wyglądać podobnie do tego:

    ![Tekstura dla boków mapy sześciennej](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png)

    Należy pamiętać, że Mapa odbicia nie musi być realistyczna, aby była skuteczna. na przykład mapa modułu użyta do utworzenia obrazów w tym artykule zawiera zaledwie cztery kieszenie zamiast sześciu.

5. Utwórz trzecią teksturę, która ma taki sam rozmiar jak pozostałe. Ta tekstura będzie górną częścią mapy modułu, która odnosi się do limitu powyżej tabeli bilardowej. Aby ta część odbicia była bardziej interesująca, możesz narysować światło narzutowe, aby wzmocnić odblaskówe, które zostały dodane do modułu cieniującego w poprzedniej procedurze. Tekstura powinna wyglądać podobnie do tego:

    ![Tekstura dla górnej części mapy sześciennej](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png)

   Po utworzeniu pojedynczych tekstur dla boków mapy modułów można użyć narzędzia, aby zebrać je do mapy modułu, która może być przechowywana w pojedynczej tekstury *. DDS* . Można użyć dowolnego programu, który ma utworzyć mapę modułu, o ile można zapisać mapę modułu w formacie tekstury. DDS. W tym instruktażu pokazano, jak utworzyć teksturę za pomocą narzędzia DirectX Texture, które jest częścią zestawu SDK programu DirectX 2010 dla czerwca.

### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>Aby złożyć mapę modułu za pomocą narzędzia DirectX Texture

1. W narzędziu DirectX Texture w menu głównym wybierz polecenie **plik**  >  **Nowa tekstura**. Zostanie wyświetlone okno dialogowe **Nowa tekstura** .

2. W grupie **Typ tekstury** wybierz opcję **tekstura mapy sześciennej**.

3. W grupie **Wymiary** Wprowadź poprawną wartość w **polach Szerokość** i **wysokość**, a następnie wybierz przycisk **OK**. Zostanie wyświetlony nowy dokument tekstury. Domyślnie tekstura najpierw pokazywana w dokumencie tekstury odnosi się do zera modułu **dodatnie X** .

4. Załaduj teksturę utworzoną dla boku modułu tekstury na powierzchnię modułu. W menu głównym wybierz pozycję **plik**  >  **Otwórz na tej mapy sześciennej**, wybierz teksturę utworzoną dla boku modułu, a następnie wybierz polecenie **Otwórz**.

5. Powtórz krok 4 dla powierzchni modułu **minus X**, **pozytywne Z**i **ujemne z** . Aby to zrobić, należy wyświetlić miarę, która ma zostać załadowana. Aby wyświetlić inną fasadę mapy modułu, w menu głównym wybierz polecenie **Wyświetl**  >  **powierzchnie mapy modułu**, a następnie wybierz miarę, którą chcesz wyświetlić.

6. Dla czołowej **osi Y** Załaduj teksturę utworzoną dla górnej części modułu tekstury.

7. Dla **nieujemnej czołowej osi Y** Załaduj teksturę utworzoną dla dolnej części modułu tekstury.

8. Zapisz teksturę.

   Można wyobrazić układ mapy modułu w następujący sposób:

   ![Układ mapy modułu środowiska](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png)

   Obraz u góry jest krawędzią modułu Y (+ Y). w środku, od lewej do prawej, to powierzchnie modułów-X, + Z, + X i-Z. u dołu jest głowa modułu-Y.

   Teraz można zmodyfikować cieniowanie, aby zmieszać przykład mapy modułu z resztą cieniowania.

### <a name="to-add-environment-mapping-to-your-shader"></a>Aby dodać mapowanie środowiska do programu do cieniowania

1. Zmodyfikuj cieniowanie tak, aby obejmowało wkład mapowania środowiska za pomocą mieszania dodatków. Wykres modułu cieniującego powinien wyglądać następująco:

    ![Closeup obu rodzajów programów do cieniowania odbijającego](../designers/media/gfx_shader_demo_billiard_step_4b.png)

    Należy zauważyć, że do uproszczenia grafu programu do cieniowania można użyć węzła **pomnożenie i dodanie** .

    Poniżej przedstawiono bardziej szczegółowy widok węzłów modułu cieniującego, które implementują mapowanie środowiska:

    ![Wykres modułu cieniującego z dodanym mapowaniem środowiska](../designers/media/gfx_shader_demo_billiard_step_4a.png)

2. Zastosuj teksturę utworzoną w poprzedniej procedurze przez skonfigurowanie właściwości tekstury mapy modułu. Ustaw wartość właściwości **tekstura** węzła **przykład mapy sześciennej** na **Texture2**, a następnie określ plik tekstury przy użyciu właściwości **filename** grupy właściwości **Texture2** .

3. Opcjonalnie można dostosować współczynnik odbicia kulki bilardowej przez skonfigurowanie właściwości **Output** węzła **stałego** . Aby uzyskać dostęp do właściwości węzła, zaznacz go, a następnie w oknie **Właściwości** Znajdź właściwość, do której chcesz uzyskać dostęp.

   Po zastosowaniu mapowania środowiska kulka bilardowej powinna wyglądać podobnie do tego:

   ![Closeup zamapowanej kuli bilardowej w środowisku](../designers/media/gfx_shader_demo_billiard_ball_4.png)

   W tym końcowym obrazie Zwróć uwagę na to, jak dodane efekty łączą się w celu utworzenia bardzo przekonującej kulki bilardowej. Kształt, tekstura i oświetlenie tworzą podstawowe wygląd obiektu 3W, a odblaskówe i odbicie sprawiają, że kulka bilardowej bardziej interesująca i wygląda jak część środowiska.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Projektant programu do cieniowania](../designers/shader-designer.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
