---
title: Pokrycie kodu — wyszukiwanie błędów
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd70394262a2dd19ebf32f57549b9d2b3e8ee92a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565978"
---
# <a name="troubleshoot-code-coverage"></a>Rozwiązywanie problemów z pokryciem kodu

Narzędzie do analizy pokrycia kodu w programie Visual Studio zbiera dane dla natywnych i zarządzanych zestawów (*.dll* lub *.exe* plików). Jednak w niektórych przypadkach w oknie **Wyniki pokrycia kodu** wyświetlany jest błąd podobny do "Puste wyniki wygenerowane: ...." Istnieje kilka powodów, dla których można uzyskać puste wyniki. Ten artykuł pomaga rozwiązać te problemy.

## <a name="what-you-should-see"></a>Co powinno zostać wyświetlone

Jeśli wybierzesz **polecenie Analizuj pokrycie kodu** w menu **Test,** a jeśli kompilacja i testy zostaną pomyślnie uruchomione, powinna zostać wyświetlona lista wyników w oknie **Pokrycie kodu.** Aby wyświetlić szczegółowe informacje, należy rozwinąć elementy.

![Wyniki pokrycia kodu z kolorowanki](../test/media/codecoverage1.png)

Aby uzyskać więcej informacji, zobacz [Użyj pokrycia kodu, aby określić, ile kodu jest testowany.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Możliwe przyczyny braku wyników lub wyświetlania starych wyników

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Czy masz odpowiednią wersję programu Visual Studio?

Potrzebujesz programu Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nie zostały wykonane żadne testy

Analiza&mdash;Sprawdź okno danych wyjściowych. Z listy rozwijanej **Pokaż dane wyjściowe** wybierz pozycję **Testy**. Sprawdź, czy są zarejestrowane jakieś błędy lub ostrzeżenia.

Analiza&mdash;pokrycia kodu wyjaśnienia jest wykonywana podczas testów. Zawiera ona tylko te zestawy, które są ładowane do pamięci podczas wykonywania testów. Jeśli żaden z testów są wykonywane, nie ma nic dla pokrycia kodu do raportu.

Rozdzielczość&mdash;w Eksploratorze testów wybierz pozycję **Uruchom wszystko,** aby sprawdzić, czy testy zostały pomyślnie uruchomione. Napraw wszelkie błędy przed użyciem **analizy pokrycia kodu**.

### <a name="youre-looking-at-a-previous-result"></a>Patrzysz na poprzedni wynik

Po zmodyfikowaniu i ponownym uruchomieniu testów, poprzedni wynik pokrycia kodu nadal może być widoczny, w tym kolorowanie kodu z tego starego uruchomienia.

1. Uruchom **analizę pokrycia kodu**.

2. Upewnij się, że w oknie Wyniki **pokrycia kodu** wybrano ostatni zestaw wyników.

### <a name="pdb-symbol-files-are-unavailable"></a>Pliki .pdb (symbol) są niedostępne

Analiza&mdash;Otwórz folder docelowy kompilacji (zazwyczaj *bin\debug)* i sprawdź, czy dla każdego zestawu w tym samym katalogu znajduje się plik *pdb* co plik *.dll* lub *.exe.*

Wyjaśnienie&mdash;Aparat pokrycia kodu wymaga, aby każdy zestaw miał skojarzony plik *pdb* dostępny podczas przebiegu testowego. Jeśli nie ma pliku *pdb* dla określonego zestawu, zestaw nie jest analizowany.

Plik *pdb* musi być generowany z tej samej kompilacji co pliki *dll* lub *.exe.*

Rozdzielczość&mdash;Upewnij się, że ustawienia kompilacji generują plik *pdb.* Jeśli pliki *pdb* nie są aktualizowane podczas tworzenia projektu, otwórz właściwości projektu, wybierz stronę **Kompilacja,** wybierz pozycję **Zaawansowane**i sprawdź **informacje debugowania**.

W przypadku projektów języka C++ upewnij się, że wygenerowane pliki pdb mają pełne informacje debugowania. Otwórz właściwości projektu i sprawdź, czy**debugowanie** >  **konsoli do** > debugowania**Generuj informacje debugowania** jest ustawione **na Generowanie informacji debugowania zoptymalizowanych pod kątem udostępniania i publikowania (/DEBUG:FULL)**.

Jeśli pliki *.pdb* i *dll* lub *.exe* znajdują się w różnych miejscach, skopiuj plik *pdb* do tego samego katalogu. Istnieje również możliwość skonfigurowania aparatu pokrycia kodu do wyszukiwania plików *.pdb* w innej lokalizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Użyj oprzyrządowanego lub zoptymalizowanego pliku binarnego

Analiza&mdash;Określić, czy plik binarny został poddany jakiejkolwiek formie zaawansowanej optymalizacji, takiej jak optymalizacja z przewodnikiem profilu, czy też został oprzyrządowany przez narzędzie do profilowania, takie jak *vsinstr.exe* lub *vsperfmon.exe*.

Wyjaśnienie&mdash;Jeśli zestaw został już instrumentowany lub zoptymalizowany przez inne narzędzie profilowania, zestaw jest pomijany w analizie pokrycia kodu. Analiza pokrycia kodu nie może być wykonywana w takich zestawach.

Rozdzielczość&mdash;Wyłącz optymalizację i użyj nowej kompilacji.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod nie jest zarządzany (.NET) lub nie jest kodem natywnym (C++)

Analiza&mdash;Sprawdź, czy uruchamiasz niektóre testy na kod zarządzany lub C++.

Analiza&mdash;pokrycia kodu objaśnienia w programie Visual Studio jest dostępna tylko w kodzie zarządzanym i macierzystym (C++). Jeśli pracujesz z narzędziami innych firm, niektóre lub wszystkie kod może wykonać na innej platformie.

Rozdzielczość&mdash;Brak dostępne.

### <a name="assembly-has-been-installed-by-ngen"></a>Zestaw został zainstalowany przez NGen

Analiza&mdash;Sprawdź, czy zestaw nie jest ładowany z pamięci podręcznej obrazu macierzystego.

Wyjaśnienie&mdash;Ze względu na wydajność zestawy obrazu macierzystego nie są analizowane. Aby uzyskać więcej informacji, zobacz [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Rozdzielczość&mdash;Użyj wersji MSIL zestawu. Nie przetwarzaj go za pomocą NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Niestandardowy plik .runsettings o złej składni

Analiza&mdash;Jeśli używasz niestandardowego pliku *runsettings,* może on zawierać błąd składni. Pokrycie kodu nie jest uruchamiany i okno pokrycia kodu nie otwiera się na końcu przebiegu testu lub pokazuje stare wyniki.

Wyjaśnienie&mdash;Można uruchomić testy jednostkowe za pomocą niestandardowego pliku *runsettings,* aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozdzielczość&mdash;Istnieją dwa możliwe typy usterek:

- **Błąd XML**

     Otwórz plik *runsettings* w edytorze XML programu Visual Studio. Poszukaj oznak błędów.

- **Błąd wyrażenia regularnego**

  Każdy ciąg znaków w pliku jest wyrażeniem regularnym. Przejrzyj każdy z nich pod kątem błędów, a w szczególności poszukaj:

  - Niedopasowane nawiasy (...) lub nawiasy bez ograniczeń \\(... \\). Jeśli chcesz dopasować nawiasy w ciągu wyszukiwania, musisz dodać przed nimi znak ucieczki. Na przykład, aby dopasować funkcję użycia:`.*MyFunction\(double\)`

  - Gwiazdka lub plus na początku wyrażenia. Aby dopasować dowolny ciąg znaków, użyj kropki, po której następuje gwiazdka:`.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Niestandardowy plik .runsettings z niepoprawnymi wykluczeniami

Analiza&mdash;Jeśli używasz niestandardowego pliku *runsettings,* upewnij się, że zawiera on zestaw.

Wyjaśnienie&mdash;Można uruchomić testy jednostkowe za pomocą niestandardowego pliku *runsettings,* aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozpoznawanie&mdash;Usuń `Include` wszystkie węzły z pliku *runsettings,* `Exclude` a następnie usuń wszystkie węzły. Jeśli to rozwiąże problem, umieść je z powrotem w etapach.

Upewnij się, że węzeł DataCollectors określa pokrycie kodu. Porównaj go z próbką w [Dostosuj analizę pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Niektóre kody są zawsze wyświetlane jako niepokryte

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Kod inicjowania w natywnych bibliotekach DLL jest wykonywany przed instrumentacją

Analiza&mdash;W statycznie połączony kod macierzysty, część funkcji inicjowania **DllMain** i kod, który wywołuje jest czasami wyświetlany jako nie objęte, nawet jeśli kod został wykonany.

Wyjaśnienie&mdash;Narzędzie pokrycia kodu działa przez wstawienie instrumentacji do złożenia tuż przed uruchomieniem aplikacji. W każdym zestawie załadowany wcześniej kod inicjowania w **DllMain** wykonuje tak szybko, jak ładuje się zestaw i przed uruchomieniu aplikacji. Ten kod wydaje się nie być objęte, który zazwyczaj ma zastosowanie do statycznie załadowanych zestawów.

Rozdzielczość&mdash;Brak.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
