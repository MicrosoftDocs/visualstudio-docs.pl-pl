---
title: Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297654"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools dla Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji znajdziesz rozwiązania typowych problemów dotyczących Visual Studio Tools for Unity, opisy znanych problemów i informacje ułatwiające ulepszanie Visual Studio Tools for Unity przez raportowanie błędów.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Aby rozwiązać typowe problemy z Visual Studio Tools for Unity, zobacz następujące sekcje.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrowanie z UnityVS do Visual Studio Tools for Unity  
 W przypadku migrowania z programu UnityVS do Visual Studio Tools for Unity należy wygenerować nowe rozwiązania programu Visual Studio dla projektów aparatu Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Aby migrować projekt Unity z UnityVS 1,8 do Visual Studio Tools for Unity 1,9  
  
1. Usuń stare rozwiązanie i pliki projektu z projektu środowiska Unity. W katalogu głównym projektu środowiska Unity Znajdź pliki programu Visual Studio. sln i. * proj i usuń je wszystkie.  
  
2. Zaimportuj pakiet Visual Studio Tools for Unity do projektu środowiska Unity. Aby uzyskać informacje na temat sposobu importowania pakietu rozszerzenia VSTU, zobacz Konfigurowanie Visual Studio Tools for Unity na stronie [wprowadzenie](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3. Wygeneruj nowe rozwiązanie i pliki projektu. Jeśli chcesz wygenerować te elementy teraz, w edytorze aparatu Unity w menu głównym wybierz **Visual Studio Tools**, **Wygeneruj pliki projektu**. W przeciwnym razie możesz pominąć ten krok, jeśli chcesz; Visual Studio Tools for Unity wygeneruje nowe pliki automatycznie po wybraniu **Visual Studio Tools**, **Otwórz w programie Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Program Visual Studio nie załaduje rozwiązania utworzonego Visual Studio Tools for Unity  
 Aby uzyskać więcej informacji, zobacz [odpowiedź na to pytanie StackOverflow](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows 8 program Visual Studio prosi o pobranie platformy docelowej Unity  
 UnityVS wymaga programu .NET Framework 3,5, który nie jest instalowany domyślnie w systemie Windows 8. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami w celu pobrania i zainstalowania programu .NET Framework 3,5.  
  
## <a name="known-issues"></a>Znane problemy  
 Istnieją znane problemy w Visual Studio Tools for Unity, które wynikają z tego, jak debuger współdziała z starszą wersją kompilatora języka C#. Pracujemy nad tym, aby pomóc w rozwiązaniu tych problemów, ale w międzyczasie mogą wystąpić następujące problemy.  
  
- Podczas debugowania aparat Unity czasami ulega awarii.  
  
- Podczas debugowania aparat Unity czasami zawiesza się.  
  
- Przechodzenie do i z metod czasami zachowuje się nieprawidłowo, szczególnie w iteratorach lub wewnątrz instrukcji switch.  
  
## <a name="reporting-errors"></a>Raportowanie błędów  
 Pomóż nam ulepszyć jakość Visual Studio Tools for Unity przez wysyłanie raportów o błędach w przypadku wystąpienia awarii, zawieszania lub innych błędów. Pomaga nam zbadać i rozwiązać problemy w Visual Studio Tools for Unity. Dziękujemy!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak zgłosić błąd, gdy program Visual Studio zawiesza się  
 Istnieją raporty, które program Visual Studio czasami zawiesza podczas debugowania przy użyciu Visual Studio Tools for Unity, ale potrzebujemy więcej danych, aby zrozumieć ten problem. Możesz pomóc nam zbadać, wykonując poniższe kroki.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że program Visual Studio zawiesza się podczas debugowania za pomocą Visual Studio Tools for Unity  
  
1. Otwórz nowe wystąpienie programu Visual Studio.  
  
2. Otwórz okno dialogowe Dołączanie do procesu. W nowym wystąpieniu programu Visual Studio, w menu głównym, wybierz **Debuguj**, **Dołącz do procesu**.  
  
3. Dołącz debuger do zamrożonego wystąpienia programu Visual Studio. W oknie dialogowym **Dołącz do procesu** wybierz zamrożone wystąpienie programu Visual Studio z tabeli **dostępne procesy** , a następnie wybierz przycisk **Dołącz** .  
  
4. Wstrzymaj debuger. W nowym wystąpieniu programu Visual Studio, w menu głównym, wybierz **Debuguj**, **Przerwij wszystko** lub po prostu naciśnij **kombinację klawiszy CTRL + ALT + BREAK**.  
  
5. Utwórz zrzut wątku. W okno Polecenie wprowadź następujące polecenie i naciśnij klawisz **Enter**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Może być konieczne, aby okno **polecenia** było widoczne jako pierwsze. W programie Visual Studio, w menu głównym, wybierz **Widok**, **inne**okna, **okno poleceń**.  
  
6. Na koniec Wyślij zrzut wątku do programu [vstusp@microsoft.com](mailto:vstusp@microsoft.com) wraz z opisem tego, co zostało wykonywane, gdy program Visual Studio został zablokowany.
