---
title: Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 750d96442f59c29a8e565e6b57eda292656ad1f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770326"
---
# <a name="best-practices-for-using-code-snippets"></a>Najlepsze praktyki dotyczące korzystania z wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kodzie we fragmencie kodu pokazano tylko najbardziej podstawową metodą coś zrobić. W przypadku większości aplikacji należy zmodyfikować kod do własnych aplikacji.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Zazwyczaj fragment kodu Try... CATCH w blokach catch i zgłoś ponownie wszystkie wyjątki. Może to nie być dobrym wyborem dla projektu. Dla każdego wyjątku istnieje kilka sposobów na odpowiedź. Aby uzyskać przykłady, zobacz [jak: Obsługa wyjątków za pomocą bloku try/catch (C# Programming Guide)](http://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) i [spróbuj... CATCH... Na koniec instrukcji](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).  
  
## <a name="file-locations"></a>Lokalizacje plików  
 Podczas lokalizacji plików można przystosować do aplikacji, możesz pomyśleć o następujących czynności:  
  
-   Znajdowanie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do folderu Program Files na komputerze, dlatego przechowywanie plików za pomocą pliki aplikacji mogą nie działać.  
  
-   Znajdowanie w bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (C:\\) nie jest bezpieczna. W przypadku danych aplikacji, firma Microsoft zaleca \Application folderu danych. W przypadku danych indywidualnego użytkownika aplikacji można utworzyć pliku dla każdego użytkownika w folderze dokumenty \My.  
  
-   Przy użyciu prawidłowej nazwy pliku. Możesz użyć <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> formantów, aby zmniejszyć prawdopodobieństwo nieprawidłowych nazw plików. Należy pamiętać, że między czasie użytkownik wybierze plik i czas, w kodzie manipuluje pliku, plik może być usunięty. Ponadto użytkownik nie może mieć uprawnienia do zapisu do pliku.  
  
## <a name="security"></a>Zabezpieczenia  
 Jak bezpieczne wstawka to zależy od tego, gdzie jest używana w kodzie źródłowym i jak zmienić po w kodzie. Poniższa lista zawiera kilka obszarów, które muszą być rozważone.  
  
- Dostęp do plików i bazy danych  
  
- Zabezpieczenia dostępu kodu  
  
- Ochrona zasobów (takich jak dzienniki zdarzeń, rejestr)  
  
- Przechowywanie kluczy tajnych  
  
- Weryfikowanie danych wejściowych  
  
- Przekazywanie danych do technologii wykonywania skryptów  
  
  Aby uzyskać więcej informacji, zobacz [zabezpieczania aplikacji](../ide/securing-applications.md).  
  
## <a name="downloaded-code-snippets"></a>Fragmenty kodu z pobranego  
 Fragmenty kodu IntelliSense instalowane przez Visual Studio nie są w sobie zagrożenie bezpieczeństwa. Jednak może być utworzona zagrożenia bezpieczeństwa w Twojej aplikacji. Fragmenty kodu, pobranego z Internetu, powinny być traktowane jak inne pobranej zawartości — z najwyższą ostrożnością.  
  
-   Pobierz fragmenty tylko z lokacji, której możesz zaufać i używać aktualnych przed wirusami.  
  
-   Otworzyć wszystkie pliki pobrane fragment kodu w Notatniku lub edytorze XML programu Visual Studio i uważnie przeczytać przed zainstalowaniem ich. Zwróć uwagę na następujące kwestie:  
  
    -   Fragment kodu uszkodzenie systemu, jeśli zostanie wykonana. Należy uważnie przeczytać kodu źródłowego, przed jego uruchomieniem.  
  
    -   Blok adresu URL pomocy plik fragmentu kodu może zawierać adresy URL, których wykonanie pliku złośliwy skrypt lub wyświetlić obraźliwe witryny sieci Web.  
  
    -   Fragment może zawierać odwołania, które są dodawane w trybie dyskretnym do projektu i mogą być ładowane z dowolnego miejsca w systemie. Te odwołania mógł zostać pobrany na komputer, z którego został pobrany fragmentu kodu. Fragment kodu może następnie wprowadzić wywołanie do metody odwołania, który jest wykonywany złośliwego kodu. Aby zabezpieczyć się przed takimi atakami, należy sprawdzić bloki Importy i odwołania do pliku fragmentu kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Fragmenty kodu IntelliSense w języku Visual Basic](http://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)   
 [Zabezpieczanie aplikacji](../ide/securing-applications.md)   
 [Fragmenty kodu](../ide/code-snippets.md)
