---
title: Najlepsze praktyki dotyczące korzystania z wstawek kodu
description: Dowiedz się więcej o fragmentach kodu, zamiarach fragmentu kodu i sposobach ich użycia w aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad94fb8ea4dffcd0c3c7c10bb06046d5558baa1e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836504"
---
# <a name="best-practices-for-using-code-snippets"></a>Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu

Kod w fragmencie kodu przedstawia tylko najbardziej podstawowy sposób wykonania czegoś. W przypadku większości aplikacji należy zmodyfikować kod w celu dostosowania go do aplikacji.

## <a name="handling-exceptions"></a>Obsługa wyjątków

Zazwyczaj fragment kodu spróbuje... Bloki catch przechwytują i ponownie generują wszystkie wyjątki. To może nie być właściwy wybór dla projektu. Dla każdego wyjątku istnieje kilka sposobów odpowiedzi. Aby zapoznać się z przykładami, zobacz [jak: obsłużyć wyjątek przy użyciu instrukcji try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) i [try... Catch... Finally — instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Lokalizacje plików

W przypadku adaptacji lokalizacji plików do aplikacji należy wziąć pod uwagę następujące kwestie:

- Znajdowanie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do folderu *Program Files* komputera, dlatego przechowywanie plików z plikami aplikacji może nie zadziałało.

- Znajdowanie bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (*C: \\*) nie jest bezpieczne. W przypadku danych aplikacji zalecamy użycie folderu *dane aplikacji* . W przypadku poszczególnych danych użytkownika aplikacja może utworzyć plik dla każdego użytkownika w folderze *dokumenty* .

- Przy użyciu prawidłowej nazwy pliku. Możesz użyć <xref:System.Windows.Forms.OpenFileDialog> formantów i, <xref:System.Windows.Forms.SaveFileDialog> Aby zmniejszyć prawdopodobieństwo wystąpienia nieprawidłowych nazw plików. Należy pamiętać, że od momentu, gdy użytkownik wybierze plik i gdy kod manipuluje plikiem, plik może zostać usunięty. Ponadto użytkownik może nie mieć uprawnień do zapisu w pliku.

## <a name="security"></a>Zabezpieczenia

Jak bezpieczny fragment kodu jest zależny od tego, gdzie jest używany w kodzie źródłowym i jak jest modyfikowany, gdy jest on w kodzie. Poniższa lista zawiera kilka obszarów, które należy wziąć pod uwagę.

- Dostęp do plików i baz danych

- Zabezpieczenia dostępu kodu

- Ochrona zasobów (takich jak dzienniki zdarzeń, rejestr)

- Przechowywanie wpisów tajnych

- Weryfikowanie danych wejściowych

- Przekazywanie danych do technologii tworzenia skryptów

Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Pobrane fragmenty kodu

Fragmenty kodu IntelliSense instalowane przez program Visual Studio nie są zagrożeniami bezpieczeństwa. Jednak mogą tworzyć zagrożenia bezpieczeństwa w aplikacji. Fragmenty kodu pobrane z Internetu powinny być traktowane jak każda inna pobrana zawartość — z największą ostrożnością.

- Pobierz fragmenty kodu z zaufanych witryn i korzystaj z aktualnego oprogramowania antywirusowego.

- Otwórz wszystkie pobrane pliki fragmentów kodu w Notatniku lub edytorze XML programu Visual Studio i uważnie przejrzyj je przed ich zainstalowaniem. Wyszukaj następujące problemy:

  - Kod wstawki może uszkodzić system w przypadku jego wykonania. Uważnie czytaj kod źródłowy przed uruchomieniem go.

  - Blok adresu URL pomocy pliku fragmentu kodu może zawierać adresy URL, które wykonują złośliwy plik skryptu lub wyświetlają obraźliwą witrynę sieci Web.

  - Fragment kodu może zawierać odwołania, które są dodawane w trybie dyskretnym do projektu i mogą być ładowane z dowolnego miejsca w systemie. Te odwołania mogły zostać pobrane na komputer z lokalizacji, w której pobrano fragment kodu. Fragment kodu może następnie wykonać wywołanie metody w odwołaniu, które wykonuje złośliwy kod. Aby zapewnić sobie ochronę przed takimi atakami, przejrzyj bloki Importy i odwołania pliku fragmentu kodu.

## <a name="see-also"></a>Zobacz też

- [Visual Basic fragmenty kodu IntelliSense](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Zabezpieczanie aplikacji](../ide/securing-applications.md)
- [Fragmenty kodu](../ide/code-snippets.md)
