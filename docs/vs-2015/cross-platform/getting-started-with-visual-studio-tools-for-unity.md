---
title: Wprowadzenie z Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
caps.latest.revision: 12
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: f110b8d6f7ab05d5a1b6942cd9ec599a8d8619b7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299824"
---
# <a name="getting-started-with-visual-studio-tools-for-unity"></a>Wprowadzenie do narzędzi Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji dowiesz się, jak zainstalować Visual Studio Tools for Unity i skonfigurować projekt Unity do pracy z programem Visual Studio.  
  
> [!IMPORTANT]
> Unity 5,2 dodaje wbudowaną obsługę Visual Studio Tools for Unity 2,1, która upraszcza konfigurację projektu. Aby móc korzystać z tej funkcji, w systemie Windows musi być wymagana wersja 5.2.0 lub nowsza, a Visual Studio Tools for Unity w wersji 2,1 lub nowszej.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby korzystać z Visual Studio Tools for Unity, potrzebne są:  
  
- Wersja programu **Visual Studio** , która obsługuje rozszerzenia, takie jak Visual Studio Community, Professional, Premium lub Enterprise. Program Visual Studio Community można pobrać bezpłatnie.  
  
     [Pobierz program Visual Studio Community](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
- Aparat **Unity** w wersji 4.0.0 lub nowszej; W wersji 5.2.0 lub nowszej w celu skorzystania z wbudowanej obsługi Visual Studio Tools for Unity **w wersji 2,1** lub nowszej.  
  
     [Pobierz środowisko Unity](https://unity3d.com/get-unity/download)  
  
## <a name="install-visual-studio-tools-for-unity"></a>Zainstaluj Visual Studio Tools for Unity  
 Pobierz i zainstaluj Visual Studio Tools for Unity z galerii programu Visual Studio. Musisz zainstalować odpowiedni pakiet dla używanej wersji programu Visual Studio. Upewnij się, że instalujesz program Visual Studio Tools for Unity w wersji 2,1 lub nowszej, aby skorzystać z wbudowanej obsługi rozszerzenia VSTU w środowisku Unity 5,2 lub nowszym.  
  
- For Visual Studio 2015 Community, Visual Studio 2015 Professional, or Visual Studio 2015 Enterprise:  
  
     [Pobierz narzędzia programu Visual Studio 2015 dla aparatu Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)  
  
- For Visual Studio 2013 Community, Visual Studio 2013 Professional, or Visual Studio 2013 Premium:  
  
     [Pobierz Visual Studio 2013 narzędzia dla aparatu Unity](https://visualstudiogallery.msdn.microsoft.com/20b80b8c-659b-45ef-96c1-437828fe7cf2)  
  
- Dla programu Visual Studio 2012 Professional lub Visual Studio 2012 Premium:  
  
     [Pobierz narzędzia programu Visual Studio 2012 dla aparatu Unity](https://visualstudiogallery.msdn.microsoft.com/7ab11d2a-f413-4ed6-b3de-ff1d05157714)  
  
- For Visual Studio 2010 Professional or Visual Studio 2010 Premium:  
  
     [Pobierz narzędzia programu Visual Studio 2010 dla aparatu Unity](https://visualstudiogallery.msdn.microsoft.com/6e536faa-ce73-494a-a746-6a14753015f1)  
  
> [!NOTE]
> Wersje Express programu Visual Studio nie obsługują rozszerzeń takich jak Visual Studio Tools for Unity. Visual Studio Community to bezpłatna wersja programu Visual Studio, która obsługuje Visual Studio Tools for Unity i inne rozszerzenia. W przypadku większości użytkowników program Visual Studio Community jest lepszym rozwiązaniem niż Express.  
  
## <a name="your-first-unity-project-with-visual-studio-tools-for-unity"></a>Twój pierwszy projekt Unity z Visual Studio Tools for Unity  
 Teraz, gdy masz wszystko, czego potrzebujesz, możesz przystąpić do pierwszego projektu środowiska Unity przy użyciu programu Visual Studio. Konfigurowanie projektu środowiska Unity jest inne w zależności od tego, które wersje aparatu Unity i Visual Studio Tools for Unity są zainstalowane. Wykonaj poniższe kroki dla zainstalowanej wersji środowiska Unity i Visual Studio Tools for Unity.  
  
### <a name="unity-52-and-higher-requires-vstu-21-or-higher"></a>Unity 5,2 i nowsze (wymaga rozszerzenia VSTU 2,1 lub nowszego)  
 Począwszy od aparatu Unity 5,2, nie trzeba już importować Visual Studio Tools UNITYPACKAGE do projektów. Jeśli projekt zaimportuje ten UNITYPACKAGE, środowisko Unity 5,2 ignoruje go i bezpośrednio ładuje Visual Studio Tools for Unity z lokalizacji instalacji.  
  
#### <a name="1---create-a-unity-project"></a>1 — Tworzenie projektu środowiska Unity  
 Jeśli już masz doświadczenie w środowisku Unity, możesz utworzyć nowy projekt lub załadować jeden z nich. W przypadku ładowania projektu, który zaimportował Visual Studio Tools UNITYPACKAGE do użycia Visual Studio Tools for Unity z poprzednią wersją aparatu Unity, zalecamy jego usunięcie przez usunięcie katalogu UnityVS.  
  
 W przeciwnym razie, jeśli jesteś nowym programem Unity, Zacznij od małego samouczka. Odwiedź stronę uczenie aparatu Unity, aby znaleźć samouczki dotyczące przykładowych projektów, z których możesz się zacząć, i lekcje, z których możesz się dowiedzieć, aby utworzyć własną grę z użyciem aparatu Unity. Na stronie Dowiedz się, jak zapoznać się z samouczkami dotyczącymi kilku różnych gier.  
  
 [Samouczki — Strona uczenia aparatu Unity](https://learn.unity.com/tutorials)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 — Konfigurowanie edytora aparatu Unity do używania Visual Studio Tools for Unity  
 Aby umożliwić projektowi używanie Visual Studio Tools for Unity, po prostu Ustaw program Visual Studio jako zewnętrzny edytor skryptów. W edytorze aparatu Unity w menu głównym wybierz polecenie **Edytuj, preferencje**; następnie w oknie dialogowym **Preferencje aparatu Unity** wybierz pozycję **narzędzia zewnętrzne**. Następnie ustaw właściwość **zewnętrzny edytor skryptów** na wersję programu Visual Studio, której chcesz użyć (Visual Studio Tools for Unity musi być zainstalowana dla tej wersji programu Visual Studio) i upewnij się, że właściwość **dołączania edytora** jest ustawiona.  
  
 Aby upewnić się, że Wbudowana obsługa Visual Studio Tools for Unity jest teraz włączona, zobacz okno dialogowe **Informacje o aparacie Unity** . W edytorze aparatu Unity, w menu głównym, wybierz **Pomoc, informacje o aparacie Unity.** Jeśli Visual Studio Tools for Unity jest zainstalowana i poprawnie skonfigurowana, zobaczysz komunikat wyświetlany w lewym dolnym rogu okna dialogowego **Informacje o aparacie Unity** .  
  
 Na koniec upewnij się, że ustawiono element docelowy kompilacji za pomocą strony **ustawień kompilacji** , a **debugowanie skryptu** jest włączone.  
  
 ![Skonfiguruj ustawienia kompilacji aparatu Unity na potrzeby debugowania.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-the-unity-editor"></a>3 — Uruchamianie programu Visual Studio z poziomu edytora aparatu Unity  
 Począwszy od aparatu Unity 5,2, menu rozszerzenia **Visual Studio Tools** nie jest już potrzebne do uruchomienia programu Visual Studio lub w celu skonfigurowania Visual Studio Tools for Unity. Zamiast tego, gdy program Visual Studio jest skonfigurowany jako zewnętrzny edytor skryptów, wystarczy wybrać plik skryptu z edytora Unity, a kod zostanie otwarty w programie Visual Studio.  
  
### <a name="previous-versions-of-unity-pre-52"></a>Poprzednie wersje aparatu Unity (sprzed 5,2)  
 Przed zastosowaniem aparatu Unity 5,2 nie ma wbudowanego wsparcia dla Visual Studio Tools for Unity. Zamiast tego każdy projekt musiał zaimportować Visual Studio Tools UNITYPACKAGE i skonfigurować inne ustawienia projektu, aby można było używać Visual Studio Tools for Unity.  
  
#### <a name="1---create-a-unity-project"></a>1 — Tworzenie projektu środowiska Unity  
 Jeśli już masz doświadczenie w środowisku Unity, możesz utworzyć nowy projekt lub załadować jeden z nich. Jeśli uruchamiasz nowy projekt, zaimportuj Visual Studio Tools UNITYPACKAGE podczas jego tworzenia.  
  
 W przeciwnym razie, jeśli jesteś nowym programem Unity, Zacznij od małego samouczka. Odwiedź stronę uczenie aparatu Unity, aby znaleźć samouczki dotyczące przykładowych projektów, z których możesz się zacząć, i lekcje, z których możesz się dowiedzieć, aby utworzyć własną grę z użyciem aparatu Unity. Na stronie Dowiedz się, jak zapoznać się z samouczkami dotyczącymi kilku różnych gier.  
  
 [Samouczki — Strona uczenia aparatu Unity](https://learn.unity.com/tutorials)  
  
#### <a name="2---configure-unity-editor-to-use-visual-studio-tools-for-unity"></a>2 — Konfigurowanie edytora aparatu Unity do używania Visual Studio Tools for Unity  
 Jeśli zaczynasz od istniejącego projektu Unity lub nie zaimportowano Visual Studio Tools UNITYPACKAGE podczas tworzenia projektu, należy zaimportować UNITYPACKAGE teraz. W edytorze aparatu Unity w menu głównym wybierz pozycję **zasoby, pakiet importowania, narzędzia programu Visual Studio 2015** (powinna zostać wyświetlona opcja dla zainstalowanej wersji programu Visual Studio).  
  
 ![Zaimportuj pakiet rozszerzenia VSTU do projektu aparatu Unity.](../cross-platform/media/vstu-configure-unity-import-vstu.png "vstu_configure_unity_import_vstu")  
  
 Na koniec upewnij się, że ustawiono element docelowy kompilacji za pomocą strony **ustawień kompilacji** , a **debugowanie skryptu** jest włączone.  
  
 ![Skonfiguruj ustawienia kompilacji aparatu Unity na potrzeby debugowania.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
#### <a name="3---launch-visual-studio-from-unity-editor"></a>3 — Uruchamianie programu Visual Studio z edytora Unity  
 Ostatnim krokiem jest uruchomienie programu Visual Studio z aparatu Unity. Spowoduje to utworzenie rozwiązania programu Visual Studio dla projektu, a następnie otwarcie go w programie Visual Studio.  
  
 W edytorze aparatu Unity w menu głównym wybierz **Visual Studio Tools, Otwórz w programie Visual Studio**.  
  
 ![Otwórz projekt środowiska Unity w programie Visual Studio.](../cross-platform/media/vstu-configure-open-in-visual-studio.png "vstu_configure_open_in_visual_studio")  
  
## <a name="next-steps"></a>Kolejne kroki  
 Aby dowiedzieć się, jak korzystać z i debugować projekt Unity w programie Visual Studio, zobacz [Using Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Strona główna środowiska Unity](https://unity.com/)
