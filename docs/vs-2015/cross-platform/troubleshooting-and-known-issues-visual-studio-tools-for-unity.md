---
title: Rozwiązywanie problemów i znane problemy (Visual Studio Tools for Unity) | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297654"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools dla Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji możesz znaleźć rozwiązania typowych problemów z narzędziami Visual Studio Tools for Unity, opisy znanych problemów i Dowiedz się, jak możesz pomóc ulepszyć program Visual Studio Tools for Unity raportowanie błędów.  
  
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
 Są to znane problemy w Visual Studio Tools for Unity, wynikiem sposobu interakcji debuger aparatu Unity w starszej wersji kompilatora języka C#. Pracujemy nad tym, aby pomóc w rozwiązaniu tych problemów, ale w międzyczasie mogą wystąpić następujące problemy.  
  
- Podczas debugowania, ulega awarii czasem platformy Unity.  
  
- Podczas debugowania, czasami zawiesza się Unity.  
  
- Przechodzenie krok po kroku do i z metody czasami zachowuje się nieprawidłowo, szczególnie w Iteratory lub wewnątrz instrukcji switch.  
  
## <a name="reporting-errors"></a>Raportowanie błędów  
 Pomóż nam ulepszyć jakość programu Visual Studio Tools for Unity przez wysyłanie raportów o błędach, gdy wystąpią uległa awarii, zawiesza się lub inne błędy. Ułatwia to nam Badaj i rozwiązuj problemy w programie Visual Studio Tools for Unity. Dziękuję!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak zgłosić błąd, gdy program Visual Studio zawiesza się  
 Brak raportów, które program Visual Studio z czasami zawiesza się podczas debugowania za pomocą programu Visual Studio Tools for Unity, ale musimy większej ilości danych, aby zrozumieć ten problem. Możesz pomóc nam przeanalizować problem przez następujące kroki.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że program Visual Studio zawiesza się podczas debugowania przy użyciu programu Visual Studio Tools for Unity  
  
1. Otwórz nowe wystąpienie programu Visual Studio.  
  
2. Otwórz dialogowym Dołącz do procesu. W wystąpieniu programu Visual Studio, w menu głównym wybierz **debugowania**, **dołączyć do procesu**.  
  
3. Dołącz debuger do zamrożone wystąpieniu programu Visual Studio. W **dołączyć do procesu** okno dialogowe, wybierz zamrożone wystąpienie programu Visual Studio z **dostępne procesy** tabeli, a następnie wybierz **Dołącz** przycisku.  
  
4. Zatrzymaj debuger. W nowym wystąpieniu programu Visual Studio, w menu głównym, wybierz **Debuguj**, **Przerwij wszystko** lub po prostu naciśnij **kombinację klawiszy CTRL + ALT + BREAK**.  
  
5. Utwórz zrzutu wątku. W okno Polecenie wprowadź następujące polecenie i naciśnij klawisz **Enter**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Konieczne może być **polecenia** okna pierwszy widoczne. W programie Visual Studio, w menu głównym wybierz **widoku**, **Windows inne**, **okna polecenia**.  
  
6. Na koniec Wyślij zrzutu wątku do [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), wraz z opisem czynności wykonywanych podczas zamrożone stało się programu Visual Studio.
