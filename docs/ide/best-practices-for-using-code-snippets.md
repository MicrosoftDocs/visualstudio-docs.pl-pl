---
title: Najlepsze praktyki dotyczące korzystania z wstawek kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f106606ae00c8f22aa5948128afb8f7f27659a5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933408"
---
# <a name="best-practices-for-using-code-snippets"></a>Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu

W kodzie we fragmencie kodu pokazano tylko najbardziej podstawową metodą coś zrobić. W przypadku większości aplikacji należy zmodyfikować kod do własnych aplikacji.

## <a name="handling-exceptions"></a>Obsługa wyjątków

Zazwyczaj fragment kodu Try... CATCH w blokach catch i zgłoś ponownie wszystkie wyjątki. Może to nie być dobrym wyborem dla projektu. Dla każdego wyjątku istnieje kilka sposobów na odpowiedź. Aby uzyskać przykłady, zobacz [jak: Obsługa wyjątków za pomocą bloku try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) i [spróbuj... CATCH... Finally — instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Lokalizacje plików

Podczas lokalizacji plików można przystosować do aplikacji, możesz pomyśleć o następujących czynności:

- Znajdowanie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do *Program Files* folderu na komputerze, dlatego przechowywanie plików za pomocą aplikacji plików może nie działają.

- Znajdowanie w bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (*C:\\*) nie jest bezpieczna. W przypadku danych aplikacji zaleca się *dane aplikacji* folderu. Dla danych poszczególnych użytkowników aplikacji można utworzyć pliku dla każdego użytkownika w *dokumenty* folderu.

- Przy użyciu prawidłowej nazwy pliku. Możesz użyć <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> formantów, aby zmniejszyć prawdopodobieństwo nieprawidłowych nazw plików. Należy pamiętać, że między czasie użytkownik wybierze plik i czas, w kodzie manipuluje pliku, plik może być usunięty. Ponadto użytkownik nie może mieć uprawnienia do zapisu do pliku.

## <a name="security"></a>Zabezpieczenia

Jak bezpieczne wstawka to zależy od tego, gdzie jest używana w kodzie źródłowym i jak zmienić po w kodzie. Poniższa lista zawiera kilka obszarów, które muszą być rozważone.

- Dostęp do plików i bazy danych

- Zabezpieczenia dostępu kodu

- Ochrona zasobów (takich jak dzienniki zdarzeń, rejestr)

- Przechowywanie kluczy tajnych

- Weryfikowanie danych wejściowych

- Przekazywanie danych do technologii wykonywania skryptów

Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Fragmenty kodu z pobranego

Fragmenty kodu IntelliSense instalowane przez Visual Studio nie są w sobie zagrożenie bezpieczeństwa. Jednak może być utworzona zagrożenia bezpieczeństwa w Twojej aplikacji. Fragmenty kodu, pobranego z Internetu, powinny być traktowane jak inne pobranej zawartości — z najwyższą ostrożnością.

- Pobierz fragmenty tylko z lokacji, której możesz zaufać i używać aktualnych przed wirusami.

- Otworzyć wszystkie pliki pobrane fragment kodu w Notatniku lub edytorze XML programu Visual Studio i uważnie przeczytać przed zainstalowaniem ich. Zwróć uwagę na następujące kwestie:

    - Fragment kodu uszkodzenie systemu, jeśli zostanie wykonana. Należy uważnie przeczytać kodu źródłowego, przed jego uruchomieniem.

    - Blok adresu URL pomocy plik fragmentu kodu może zawierać adresy URL, których wykonanie pliku złośliwy skrypt lub wyświetlić obraźliwe witryny sieci Web.

    - Fragment może zawierać odwołania, które są dodawane w trybie dyskretnym do projektu i mogą być ładowane z dowolnego miejsca w systemie. Te odwołania mógł zostać pobrany na komputer, z którego został pobrany fragmentu kodu. Fragment kodu może następnie wprowadzić wywołanie do metody odwołania, który jest wykonywany złośliwego kodu. Aby zabezpieczyć się przed takimi atakami, należy sprawdzić bloki Importy i odwołania do pliku fragmentu kodu.

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu IntelliSense w języku Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Zabezpieczanie aplikacji](../ide/securing-applications.md)
- [Fragmenty kodu](../ide/code-snippets.md)