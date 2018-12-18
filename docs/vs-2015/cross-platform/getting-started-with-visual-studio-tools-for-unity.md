---
title: Wprowadzenie do narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 9ed6cb4127ba57c6b9b84a32996968dbf9fac4fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762720"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Wprowadzenie do narzędzi Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W tej sekcji dowiesz się, jak zainstalować program Visual Studio Tools for Unity i skonfigurować swoim projekcie aparatu Unity do pracy z programem Visual Studio.  
  
> [!IMPORTANT]
>  Unity 5.2 dodaje wbudowaną obsługę programu Visual Studio Tools for Unity 2.1, która upraszcza ustawienia projektu. Aby móc korzystać z tego, będziesz potrzebować Unity wersji 5.2.0 lub nowszej na Windows i Visual Studio Tools for Unity w wersji 2.1 lub wyższej.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć Visual Studio Tools for Unity, będą potrzebne:  
  
-   Wersja **programu Visual Studio** obsługujący rozszerzenia, takie jak Visual Studio Community, Professional, Premium lub Enterprise. Program Visual Studio Community można pobrać za darmo.  
  
     [Pobierz program Visual Studio Community](http://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   **Unity** wersji 4.0.0 lub wyższy. **Unity** wersji 5.2.0 lub nowszej, aby skorzystać z wbudowanej obsługi narzędzi Visual Studio Tools for Unity w wersji 2.1 lub wyższej.  
  
     [Pobierz oprogramowanie Unity](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Instalowanie narzędzia Visual Studio Tools for Unity  
 Pobierz i zainstaluj program Visual Studio Tools for Unity z galerii Visual Studio. Musisz zainstalować odpowiedni pakiet dla używanej wersji programu Visual Studio. Upewnij się zainstalować Visual Studio Tools for Unity w wersji 2.1 lub nowszej móc korzystać z wbudowaną obsługą VSTU w Unity 5.2 lub nowszej.  
  
-   For Visual Studio 2015 Community, Visual Studio 2015 Professional, or Visual Studio 2015 Enterprise:  
  
     [Pobierz program Visual Studio 2015 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
-   For Visual Studio 2013 Community, Visual Studio 2013 Professional, or Visual Studio 2013 Premium:  
  
     [Pobierz program Visual Studio 2013 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
-   W przypadku programu Visual Studio 2012 Professional lub Visual Studio 2012 Premium:  
  
     [Pobierz program Visual Studio 2012 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
-   For Visual Studio 2010 Professional or Visual Studio 2010 Premium:  
  
     [Pobierz program Visual Studio 2010 Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
>  Wersje Express programu Visual Studio nie obsługują rozszerzenia, takie jak Visual Studio Tools for Unity. Program Visual Studio Community jest bezpłatną wersję programu Visual Studio, który obsługuje Visual Studio Tools for Unity i inne rozszerzenia. Dla większości użytkowników programu Visual Studio Community jest lepszym rozwiązaniem niż Express.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Pierwszego projektu środowiska Unity za pomocą programu Visual Studio Tools for Unity  
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz przystąpić do pierwszego projektu środowiska Unity za pomocą programu Visual Studio. Konfigurowanie projektu środowiska Unity jest różne w zależności od tego, które wersje aparatu Unity i programu Visual Studio Tools for Unity są zainstalowane. Wykonaj poniższe kroki dla wersji aparatu Unity i Visual Studio Tools for Unity, który został zainstalowany.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5.2 lub nowszej (wymaga VSTU 2.1 lub nowszej)  
 Począwszy od Unity 5.2, masz już do zaimportowania unitypackage narzędzia programu Visual Studio w swoich projektach. Jeśli projekt importuje tego unitypackage, Unity 5.2 je ignoruje i bezpośrednio ładuje programu Visual Studio Tools for Unity z jego lokalizacji instalacji.  
  
#### <a name="1---create-a-unity-project"></a>1 — Tworzenie projektu środowiska Unity  
 Jeśli masz już doświadczenie w pracy z aparatu Unity, możesz utworzyć nowy projekt lub załadować własny. W przypadku ładowania projektu, który zaimportowany unitypackage narzędzia programu Visual Studio za pomocą programu Visual Studio Tools for Unity poprzednią wersję aparatu Unity, zaleca się usunąć przez usunięcie katalogu UnityVS.  
  
 W przeciwnym razie jeśli jesteś nowym użytkownikiem platformy Unity, zacząć od małej od podstawowego samouczka. Odwiedź stronę Unity Dowiedz się, aby znaleźć samouczki dotyczące przykładowych projektów, które można uruchomić przy użyciu i lekcje, których można uzyskać z poziomu, aby tworzyć gry przy użyciu aparatu Unity. Dowiedz się, Unity strona ma samouczki łatwe do wykonania dla kilku różnych gier.  
  
 [Samouczki — strona Unity Dowiedz się więcej](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 — Konfigurowanie Edytor platformy Unity można użyć programu Visual Studio Tools for Unity  
 Aby włączyć projekt do programu Visual Studio Tools for Unity, zestawu Visual Studio jako jego Edytor skryptu zewnętrznego. W edytorze Unity w menu głównym wybierz **Edycja preferencji**; następnie w **preferencje Unity** okno dialogowe, wybierz **zewnętrznych narzędzi**. Następnym etapem jest skonfigurowanie **Edytor skryptów zewnętrznych** właściwości do wersji programu Visual Studio, w której chcesz użyć (dla tej wersji programu Visual Studio musi być zainstalowany program Visual Studio Tools for Unity) i upewnij się, że **edytora dołączanie** właściwość jest ustawiona.  
  
 Aby upewnić się, że wbudowane wsparcie dla Visual Studio Tools dla aparatu Unity jest teraz włączony, zobacz **o Unity** okna dialogowego. W oknie Edytor środowiska Unity w menu głównym wybierz **pomocy dotyczące aparatu Unity.** Jeśli program Visual Studio Tools for Unity jest zainstalowany i poprawnie skonfigurowany, zobaczysz komunikat wyświetlany w lewym dolnym rogu **o Unity** okna dialogowego.  
  
 Na koniec upewnij się, został ustawiony element docelowy kompilacji, za pośrednictwem **ustawieniach kompilacji** strony oraz że **debugowanie skryptu** jest włączona.  
  
 ![Konfigurowanie ustawień kompilacji platformy Unity na potrzeby debugowania. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3 — Uruchom program Visual Studio Edytor platformy Unity  
 Począwszy od Unity 5.2 **Visual Studio Tools** menu rozszerzeń nie są już potrzebne do uruchomienia programu Visual Studio lub aby skonfigurować program Visual Studio Tools for Unity. Zamiast tego po skonfigurowaniu programu Visual Studio jako edytora skryptu zewnętrznego, po prostu wybierz plik skryptu z programu Unity editor, a kod zostanie otwarty w programie Visual Studio.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Poprzednie wersje aparatu Unity (pre-5.2)  
 Przed Unity 5.2 wystąpił brak wbudowanej obsługi narzędzi Visual Studio Tools for Unity. Zamiast tego każdy projekt miał importować unitypackage Visual Studio Tools i skonfigurować inne ustawienia projektu, aby można było używać programu Visual Studio Tools for Unity.  
  
#### <a name="1---create-a-unity-project"></a>1 — Tworzenie projektu środowiska Unity  
 Jeśli masz już doświadczenie w pracy z aparatu Unity, możesz utworzyć nowy projekt lub załadować własny. Jeśli Trwa uruchamianie nowego projektu, należy zaimportować unitypackage narzędzia programu Visual Studio, podczas jego tworzenia.  
  
 W przeciwnym razie jeśli jesteś nowym użytkownikiem platformy Unity, zacząć od małej od podstawowego samouczka. Odwiedź stronę Unity Dowiedz się, aby znaleźć samouczki dotyczące przykładowych projektów, które można uruchomić przy użyciu i lekcje, których można uzyskać z poziomu, aby tworzyć gry przy użyciu aparatu Unity. Dowiedz się, Unity strona ma samouczki łatwe do wykonania dla kilku różnych gier.  
  
 [Samouczki — strona Unity Dowiedz się więcej](http://unity3d.com/learn/tutorials/modules)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 — Konfigurowanie Edytor platformy Unity można użyć programu Visual Studio Tools for Unity  
 Jeśli zaczynasz z istniejącego projektu środowiska Unity lub podczas tworzenia projektu zaimportowano unitypackage narzędzia programu Visual Studio, musisz zaimportować unitypackage teraz. W oknie Edytor środowiska Unity w menu głównym wybierz **zasobów, importowanie pakietu Visual Studio 2015 Tools** (powinien zostać wyświetlony opcji wersji ma zainstalowanego programu Visual Studio).  
  
 ![Importuj pakiet w narzędziach VSTU w swoim projekcie aparatu Unity. ](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Na koniec upewnij się, został ustawiony element docelowy kompilacji, za pośrednictwem **ustawieniach kompilacji** strony oraz że **debugowanie skryptu** jest włączona.  
  
 ![Konfigurowanie ustawień kompilacji platformy Unity na potrzeby debugowania. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3 — Uruchom program Visual Studio z edytora aparatu Unity  
 Ostatnim krokiem jest do uruchamiania programu Visual Studio z poziomu aparatu Unity. Tworzy rozwiązanie Visual Studio dla projektu, a następnie zostanie otwarty w programie Visual Studio.  
  
 W edytorze Unity w menu głównym wybierz **narzędzia programu Visual Studio, Otwórz w programie Visual Studio**.  
  
 ![Otwórz swój projekt środowiska unity w programie Visual Studio. ](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak pracować z i debugowanie projektu środowiska Unity w programie Visual Studio, zobacz [przy użyciu programu Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Strona główna aparatu Unity](http://unity3d.com)

