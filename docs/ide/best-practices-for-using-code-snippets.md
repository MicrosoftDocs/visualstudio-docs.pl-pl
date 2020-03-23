---
title: Najlepsze praktyki dotyczące korzystania z wstawek kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08add20b59e3e14897d1870aa45fd6cce8698d96
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591713"
---
# <a name="best-practices-for-using-code-snippets"></a>Najważniejsze wskazówki dotyczące używania fragmentów kodu

Kod we fragmentie kodu pokazuje tylko najbardziej podstawowy sposób, aby coś zrobić. W przypadku większości aplikacji kod musi być modyfikowany w celu dopasowania do aplikacji.

## <a name="handling-exceptions"></a>Obsługa wyjątków

Zazwyczaj fragment kodu Spróbuj... Catch bloki catch i rethrow wszystkie wyjątki. To może nie być właściwy wybór dla twojego projektu. Dla każdego wyjątku istnieje kilka sposobów, aby odpowiedzieć. Na przykład zobacz [Jak: Obsługa wyjątku przy użyciu try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) i [Try... Złapać... Instrukcja Finally (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Lokalizacje plików

Podczas dostosowywania lokalizacji plików do aplikacji należy pomyśleć o następujących tematach:

- Znalezienie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do folderu *Pliki programów* na komputerze, więc przechowywanie plików z plikami aplikacji może nie działać.

- Znalezienie bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (*C:\\*) nie jest bezpieczne. W przypadku danych aplikacji zaleca się folder *Dane aplikacji.* W przypadku poszczególnych danych użytkownika aplikacja może utworzyć plik dla każdego użytkownika w folderze *Dokumenty.*

- Przy użyciu prawidłowej nazwy pliku. Można użyć <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> formanty, aby zmniejszyć prawdopodobieństwo nieprawidłowych nazw plików. Należy pamiętać, że między czasem użytkownik wybiera plik i czas kodu manipuluje plikiem, plik może zostać usunięty. Ponadto użytkownik może nie mieć uprawnień do zapisu w pliku.

## <a name="security"></a>Zabezpieczenia

Jak bezpieczny jest fragment kodu zależy od tego, gdzie jest używany w kodzie źródłowym i jak jest modyfikowany, gdy jest w kodzie. Poniższa lista zawiera kilka obszarów, które należy wziąć pod uwagę.

- Dostęp do plików i bazy danych

- Zabezpieczenia dostępu do kodu

- Ochrona zasobów (takich jak dzienniki zdarzeń, rejestr)

- Przechowywanie wpisów tajnych

- Weryfikowanie danych wejściowych

- Przekazywanie danych do technologii skryptów

Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Pobrane fragmenty kodu

Fragmenty kodu IntelliSense zainstalowane przez program Visual Studio nie stanowią zagrożenia dla bezpieczeństwa. Mogą one jednak stwarzać zagrożenia bezpieczeństwa w aplikacji. Fragmenty pobrane z Internetu powinny być traktowane jak każda inna pobrana zawartość - ze szczególną ostrożnością.

- Pobieraj fragmenty kodu tylko z zaufanych witryn i korzystaj z aktualnego oprogramowania antywirusowego.

- Otwórz wszystkie pobrane pliki urywków w Notatniku lub edytorze XML programu Visual Studio i przejrzyj je uważnie przed ich zainstalowaniem. Poszukaj następujących problemów:

  - Kod fragmentu kodu może uszkodzić system, jeśli go wykonasz. Przed jego uruchomieniem należy dokładnie przeczytać kod źródłowy.

  - Blok adresu URL Pomocy pliku urywka może zawierać adresy URL, które wykonują złośliwy plik skryptu lub wyświetlają obraźliwą witrynę sieci Web.

  - Fragment kodu może zawierać odwołania, które są dodawane po cichu do projektu i mogą być ładowane z dowolnego miejsca w systemie. Te odwołania mogły zostać pobrane na komputer, z którego pobrano fragment kodu. Fragment kodu może następnie wywołać metodę w odwołaniu, który wykonuje złośliwy kod. Aby chronić się przed takim atakiem, przejrzyj bloki Importi i Odwołania pliku urywka.

## <a name="see-also"></a>Zobacz też

- [Urywki kodu intellisense języka Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Zabezpieczanie aplikacji](../ide/securing-applications.md)
- [Fragmenty kodu](../ide/code-snippets.md)
