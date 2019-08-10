---
title: Pokrycie kodu — wyszukiwanie błędów
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7aef839027639770e60292210aaddf998c97fce0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926545"
---
# <a name="troubleshoot-code-coverage"></a>Rozwiązywanie problemów z pokryciem kodu

Narzędzie analizy pokrycia kodu w programie Visual Studio zbiera dane dla zestawów natywnych i zarządzanych ( *.dll* lub *.exe* plików). Jednak w niektórych przypadkach **wyniki pokrycia kodu** okno wyświetla błąd podobny do "wygenerowano puste wyniki: …" Istnieje kilka powodów dlaczego otrzymujesz puste wyniki. Ten artykuł pomaga w rozwiązaniu tych problemów.

## <a name="what-you-should-see"></a>Co powinno zostać wyświetlone

Jeśli wybierzesz **Analizuj pokrycie kodu** polecenie **testu** menu i kompilacja oraz testy zostaną wykonane pomyślnie, powinien zostać wyświetlony listy powoduje **pokrycia kodu** okno. Aby wyświetlić szczegółowe informacje, należy rozwinąć elementy.

![Wyniki pokrycia kodu za pomocą kolorowania](../test/media/codecoverage1.png)

Aby uzyskać więcej informacji, zobacz [użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Możliwe przyczyny braku wyników lub wyświetlania starych wyników

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Czy masz odpowiednią wersję programu Visual Studio?
Potrzebujesz programu Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nie zostały wykonane żadne testy

Analiza&mdash;Sprawdź okno danych wyjściowych. W **Pokaż dane wyjściowe z** listy rozwijanej wybierz **testy**. Sprawdź, czy są zarejestrowane jakieś błędy lub ostrzeżenia.

Wyjaśnienie&mdash;analizy pokrycia kodu odbywa się podczas wykonywania testów. Zawiera ona tylko te zestawy, które są ładowane do pamięci podczas wykonywania testów. Jeśli żadne testy są wykonywane, nie ma nic pokrycia kodu do raportu.

Rozpoznawanie&mdash;w Eksploratorze testów wybierz **Uruchom wszystkie** Aby sprawdzić, czy testy zostaną wykonane pomyślnie. Napraw wszelkie błędy przed użyciem **Analizuj pokrycie kodu**.

### <a name="youre-looking-at-a-previous-result"></a>Szukasz na poprzedni wynik

Podczas modyfikowania i ponownego przeprowadzania testów poprzedni wynik pokrycia kodu może nadal być widoczny, włącznie z kolorowaniem kodu z tego starego uruchamiania.

1. Uruchom analizę pokrycia kodu.

2. Upewnij się, czy wybrano najbardziej aktualnych wyników w **wyniki pokrycia kodu** okna.

### <a name="pdb-symbol-files-are-unavailable"></a>Pliki .pdb (symbol) są niedostępne

Analiza&mdash;Otwórz docelowy folder kompilacji (zazwyczaj *bin\debug*) i upewnij się, że dla każdego zestawu istnieje *.pdb* pliku w tym samym katalogu co *.dll*lub *.exe* pliku.

Wyjaśnienie&mdash;silnik pokrycia kodu wymaga, że każdy zestaw miał związanych z nią *.pdb* plików dostępny podczas przebiegu testu. Jeśli ma nie *.pdb* plik określony zestaw, zestaw nie jest analizowana.

*.Pdb* plik musi zostać wygenerowany z tej samej kompilacji co *.dll* lub *.exe* plików.

Rozpoznawanie&mdash;upewnij się, że ustawienia kompilacji generują *.pdb* pliku. Jeśli *.pdb* pliki nie są aktualizowane, gdy projekt jest kompilowany, następnie otwórz właściwości projektu, wybierz **kompilacji** wybierz **zaawansowane**i sprawdzić **Informacje debugowania**.

Jeśli *.pdb* i *.dll* lub *.exe* pliki znajdują się w różnych miejscach, kopia *.pdb* pliku, w tym samym katalogu. Użytkownik może również skonfigurować silnik pokrycia kodu, aby wyszukać *.pdb* pliki w innej lokalizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Użyj zinstrumentowanego lub zoptymalizowanego pliku binarnego

Analiza&mdash;ustalenia, czy plik binarny przeszedł dowolnej formie procesu zaawansowanej optymalizacji, takie jak Optymalizacja sterowana profilem, lub czy został instrumentowany przez narzędzia profilowania, takich jak *vsinstr.exe* lub  *vsperfmon.exe*.

Wyjaśnienie&mdash;Jeśli zestawu została już zinstrumentowany lub zoptymalizowany przez inne narzędzie profilowania, zestaw jest pominięty z analizy pokrycia kodu. Nie można wykonać analizy pokrycia kodu na takich zestawach.

Rozpoznawanie&mdash;wyłączyć optymalizację i użyj nowej kompilacji.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod nie jest zarządzany (.NET) lub nie jest kodem natywnym (C++)

Analiza&mdash;upewnij się, że używasz niektóre testy w zarządzanych lub kodu w języku C++.

Wyjaśnienie&mdash;analizy pokrycia kodu w programie Visual Studio jest dostępna tylko na zarządzanego i natywnego kodu (C++). Jeśli pracujesz z narzędziami innych firm, część lub całość kodu może być wykonywany na innej platformie.

Rozpoznawanie&mdash;niedostępne.

### <a name="assembly-has-been-installed-by-ngen"></a>Zestaw został zainstalowany przez NGen

Analiza&mdash;zweryfikować, że zestaw nie został załadowany z pamięci podręcznej obrazów natywnych.

Wyjaśnienie&mdash;ze względu na wydajność zestawy obrazu natywnego nie są analizowane. Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Rozpoznawanie&mdash;należy użyć wersji MSIL zestawu. Nie przetwarzaj go z NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Niestandardowy plik .runsettings o złej składni

Analiza&mdash;Jeśli używasz niestandardowego *.runsettings* pliku, może on zawierać błąd składni. Pokrycie kodu nie jest uruchamiane, a albo okno pokrycia kodu nie zostanie otwarte na końcu przebiegu testu lub jest on stare wyniki.

Wyjaśnienie&mdash;można uruchomić testy jednostkowe z niestandardowego *.runsettings* pliku, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozpoznawanie&mdash;istnieją dwa typy możliwych błędów:

- **Błąd XML**

     Otwórz *.runsettings* plik w edytorze programu Visual Studio XML. Poszukaj oznak błędów.

- **Błąd w wyrażeniu regularnym**

  Każdy ciąg znaków w pliku jest wyrażeniem regularnym. Przejrzyj każdy z nich błędy, a w szczególności zwróć uwagę na:

  - Niedopasowane nawiasy (...) lub nawiasy \\(...) \\). Jeśli chcesz dopasować nawiasy w ciągu wyszukiwania, musisz dodać przed nimi znak ucieczki. Na przykład, aby dopasować użycie funkcji: `.*MyFunction\(double\)`

  - Gwiazdka lub plus na początku wyrażenia. Aby dopasować dowolny ciąg znaków, należy użyć kropki poprzedzającej gwiazdkę: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Niestandardowy plik .runsettings z niepoprawnymi wykluczeniami

Analiza&mdash;Jeśli używasz niestandardowego *.runsettings* upewnij się, że zawiera on Twój zestaw.

Wyjaśnienie&mdash;można uruchomić testy jednostkowe z niestandardowego *.runsettings* pliku, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozpoznawanie&mdash;usunięcie wszystkich `Include` węzłów z *.runsettings* pliku, a następnie usuń wszystkie `Exclude` węzłów. Jeśli to rozwiąże problem, umieść je z powrotem w etapach.

Upewnij się, że węzeł DataCollectors określa pokrycie kodu. Porównaj je z przykładem w [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Niektóre kody są zawsze wyświetlane jako niepokryte

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Kod inicjowania w natywnych bibliotekach DLL jest wykonywany przed instrumentacją

Analiza&mdash;w statycznie połączonym kodzie natywnym część funkcji inicjowania **DllMain** i kod, który ją wywołuje, są czasami przedstawiane jako kod niepokryty, mimo że kod został wykonany.

Wyjaśnienie&mdash;narzędzie pokrycia kodu działa przez wstawienie Instrumentacji do zestawu, przed uruchomieniem aplikacji. W każdym zestawie załadowano wcześniej kod inicjowania w **DllMain** wykonuje zaraz po załadowaniu zestawu i przed uruchomieniem aplikacji. Ten kod zostanie wyświetlony jako niepokryty, którego zwykle dotyczy to statycznie załadowanych zestawów.

Rozpoznawanie&mdash;None.

## <a name="see-also"></a>Zobacz także

- [Użycie pokrycia kodu, aby ustalić, ile kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
