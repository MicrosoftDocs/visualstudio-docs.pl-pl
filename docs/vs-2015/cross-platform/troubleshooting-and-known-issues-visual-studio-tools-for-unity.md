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
ms.openlocfilehash: 6e1b34cbc2497bd70f65021c83db4f59480519f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62573209"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools dla Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji możesz znaleźć rozwiązania typowych problemów z narzędziami Visual Studio Tools for Unity, opisy znanych problemów i Dowiedz się, jak możesz pomóc ulepszyć program Visual Studio Tools for Unity raportowanie błędów.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Aby rozwiązać niektóre typowe problemy przy użyciu programu Visual Studio Tools for Unity, zobacz następujące sekcje.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrowania UnityVS do narzędzi Visual Studio Tools for Unity  
 W przypadku migrowania z UnityVS do programu Visual Studio Tools for Unity, należy wygenerować nowego rozwiązania programu Visual Studio dla projektów aparatu Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Przeprowadzić migrację projektu środowiska Unity z UnityVS 1.8 do Visual Studio Tools for Unity 1.9  
  
1. Usuń stare pliki rozwiązania i projektu z projektu środowiska Unity. W katalogu głównym w swoim projekcie aparatu Unity zlokalizować SLN programu Visual Studio i. * proj pliki i usunąć je wszystkie.  
  
2. Importuj Visual Studio Tools dla pakietu Unity w swoim projekcie aparatu Unity. Aby uzyskać informacje o sposobie importowania pakietów w narzędziach VSTU, zobacz Konfigurowanie programu Visual Studio Tools for Unity w [wprowadzenie](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) strony.  
  
3. Generuj nowe pliki rozwiązań i projektów. Jeśli chcesz wygenerować je teraz w edytorze Unity w menu głównym wybierz **Visual Studio Tools**, **Generuj pliki projektu**. W przeciwnym razie można pominąć ten krok, chcąc; Visual Studio Tools for Unity wygeneruje nowe pliki automatycznie po wybraniu **Visual Studio Tools**, **Otwórz w programie Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Program Visual Studio nie można załadować rozwiązania utworzonego w programie Visual Studio Tools for Unity  
 Aby uzyskać więcej informacji, zobacz [odpowiedzi na to pytanie w witrynie stackoverflow](http://stackoverflow.com/a/24035907/36702).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows 8 Visual Studio Wyświetla prośbę można pobrać platformę docelową aparatu Unity  
 UnityVS wymaga programu .net framework 3.5, który nie jest instalowany domyślnie w systemie Windows 8. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami, aby pobrać i zainstalować program .net framework 3.5.  
  
## <a name="known-issues"></a>Znane problemy  
 Są to znane problemy w Visual Studio Tools for Unity, wynikiem sposobu interakcji debuger aparatu Unity w starszej wersji kompilatora języka C#. Pracujemy nad pomóc w rozwiązaniu tych problemów, ale mogą wystąpić następujące problemy, w tym samym czasie.  
  
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
  
4. Zatrzymaj debuger. W wystąpieniu programu Visual Studio, w menu głównym wybierz **debugowania**, **Przerwij wszystko** lub po prostu naciśnij **Ctrl + Alt + Break**.  
  
5. Utwórz zrzutu wątku. W oknie wiersza polecenia wprowadź następujące polecenie i naciśnij klawisz **Enter**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Konieczne może być **polecenia** okna pierwszy widoczne. W programie Visual Studio, w menu głównym wybierz **widoku**, **Windows inne**, **okna polecenia**.  
  
6. Na koniec Wyślij zrzutu wątku do [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), wraz z opisem czynności wykonywanych podczas zamrożone stało się programu Visual Studio.
