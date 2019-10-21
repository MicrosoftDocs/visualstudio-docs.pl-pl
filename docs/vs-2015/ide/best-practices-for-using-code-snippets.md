---
title: Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 74da305b69a9561573466d385c5d7b686da3693f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620322"
---
# <a name="best-practices-for-using-code-snippets"></a>Najlepsze praktyki dotyczące korzystania z wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod w fragmencie kodu przedstawia tylko najbardziej podstawowy sposób wykonania czegoś. W przypadku większości aplikacji należy zmodyfikować kod w celu dostosowania go do aplikacji.

## <a name="handling-exceptions"></a>Obsługa wyjątków
 Zazwyczaj fragment kodu spróbuje... Bloki catch przechwytują i ponownie generują wszystkie wyjątki. To może nie być właściwy wybór dla projektu. Dla każdego wyjątku istnieje kilka sposobów odpowiedzi. Aby zapoznać się z przykładami, zobacz [How to: obsługa wyjątku przy użyciuC# instrukcji try/catch (Przewodnik programowania)](https://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) i [try... Catch... Finally — instrukcja](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).

## <a name="file-locations"></a>Lokalizacje plików
 W przypadku adaptacji lokalizacji plików do aplikacji należy wziąć pod uwagę następujące kwestie:

- Znajdowanie dostępnej lokalizacji. Użytkownicy mogą nie mieć dostępu do folderu Program Files komputera, dlatego przechowywanie plików z plikami aplikacji może nie zadziałało.

- Znajdowanie bezpiecznej lokalizacji. Przechowywanie plików w folderze głównym (C: \\) nie jest bezpieczne. W przypadku danych aplikacji zaleca się folder \Dane danych. W przypadku poszczególnych danych użytkownika aplikacja może utworzyć plik dla każdego użytkownika w folderze \Moje dokumenty.

- Przy użyciu prawidłowej nazwy pliku. Możesz użyć formantów <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog>, aby zmniejszyć prawdopodobieństwo nieprawidłowych nazw plików. Należy pamiętać, że od momentu, gdy użytkownik wybierze plik i gdy kod manipuluje plikiem, plik może zostać usunięty. Ponadto użytkownik może nie mieć uprawnień do zapisu w pliku.

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
 [Visual Basic fragmenty kodu IntelliSense](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [zabezpieczające](../ide/securing-applications.md) [fragmenty kodu](../ide/code-snippets.md) aplikacji
