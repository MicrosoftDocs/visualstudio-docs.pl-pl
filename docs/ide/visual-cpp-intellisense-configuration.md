---
title: Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 605ad454d00387d9a9094a518b4afed279fcc190
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461588"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense

W niektórych przypadkach może być konieczne ręczne skonfigurowanie C++ projektu w celu poprawnego działania funkcji IntelliSense. W przypadku projektów MSBuild (opartych na plikach vcxproj) można dostosować ustawienia we właściwościach projektu. W przypadku projektów innych niż MSBuild można dostosować ustawienia w pliku pliku cppproperties. JSON w katalogu głównym projektu. W niektórych przypadkach może być konieczne utworzenie pliku wskazówki, aby pomóc IntelliSense zrozumieć definicje makr. Środowisko IDE programu Visual Studio pomaga identyfikować i rozwiązywać problemy z technologią IntelliSense.

## <a name="single-file-intellisense"></a>Funkcja IntelliSense pojedynczego pliku

Gdy otworzysz plik, który nie jest uwzględniony w projekcie, program Visual Studio udostępnia obsługę funkcji IntelliSense, ale domyślnie nie są wyświetlane żadne z nich. Jeśli na **pasku nawigacyjnym** pojawiają się *różne pliki*, to prawdopodobnie wyjaśnia, dlaczego nie widzisz części błędów w obszarze niepoprawnego kodu lub dlaczego makro preprocesora nie jest zdefiniowane.

## <a name="check-the-error-list"></a>Sprawdź Lista błędów

Jeśli plik nie jest otwarty w trybie pojedynczego pliku, a technologia IntelliSense nie działa prawidłowo, pierwsze miejsce do sprawdzenia jest oknem Lista błędów. Aby wyświetlić wszystkie błędy funkcji IntelliSense dla bieżącego pliku źródłowego wraz ze wszystkimi dołączonymi plikami nagłówka, wybierz opcję **Kompiluj + IntelliSense** na liście rozwijanej:

![Funkcja IntelliSense języka VC + + w Lista błędów](media/vcpp-intellisense-error-list.png)

Funkcja IntelliSense da maksymalnie 1000 błędy. Jeśli w plikach nagłówkowych zawartych w pliku źródłowym występuje ponad 1000 błędów, plik źródłowy pokazuje tylko jeden błąd zygzaka na początku pliku źródłowego.

## <a name="ensure-include-paths-are-correct"></a>Upewnij się, że ścieżki #include są poprawne

### <a name="msbuild-projects"></a>Projekty MSBuild

Jeśli uruchamiasz kompilacje poza środowiskiem IDE programu Visual Studio, a kompilacje zakończą się pomyślnie, ale technologia IntelliSense jest niepoprawna, istnieje możliwość, że wiersz polecenia nie jest zsynchronizowany z ustawieniami projektu dla co najmniej jednej konfiguracji. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i upewnij się, że wszystkie ścieżki **#include** są poprawne dla bieżącej konfiguracji i platformy. Jeśli ścieżki są identyczne we wszystkich konfiguracjach i na platformach, możesz wybrać **wszystkie konfiguracje** i **wszystkie platformy** , a następnie sprawdzić, czy ścieżki są poprawne.

![Katalogi dołączania VC + +](media/vcpp-intellisense-include-paths.png)

 Aby wyświetlić bieżące wartości dla makr kompilacji, takich jak **VC_IncludePath**, zaznacz wiersz Uwzględnij katalogi i kliknij listę rozwijaną po prawej stronie. Następnie wybierz  **\<pozycję Edytuj >** i kliknij przycisk **makra** .

### <a name="makefile-projects"></a>Projekty pliku reguł dla programu make

W przypadku projektów reguł programu make, które są oparte na szablonie projektu NMake, wybierz pozycję **NMAKE** w lewym okienku, a następnie wybierz pozycję **Uwzględnij ścieżkę wyszukiwania** w kategorii **IntelliSense** :

![Ścieżki dołączania projektu pliku reguł programu make](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Otwórz projekty folderu

W przypadku projektów CMake upewnij się, że ścieżki #include są poprawnie określone dla wszystkich konfiguracji w CMakeLists. txt. Inne typy projektów mogą wymagać pliku pliku cppproperties. JSON. Aby uzyskać więcej informacji, zobacz [Konfigurowanie funkcji IntelliSense z pliku cppproperties. JSON](/cpp/build/open-folder-projects-cpp#configure-intellisense-and-browsing-hints-with-cpppropertiesjson). Upewnij się, że ścieżki są poprawne dla każdej konfiguracji, która jest zdefiniowana w pliku.

Jeśli w pliku pliku cppproperties. JSON wystąpi błąd składniowy, IntelliSense w plikach, których dotyczy problem, będzie niepoprawna. Program Visual Studio wyświetli błąd w Okno Dane wyjściowe.

## <a name="tag-parser-issues"></a>Problemy z parserem tagów

Analizator tagów jest analizatorem "rozmytego" C++ , który jest używany do przeglądania i nawigowania. Jest bardzo szybka, ale nie próbuje całkowicie comprehend każdej konstrukcji kodu.

Na przykład nie szacuje makra preprocesora i w związku z tym może nieprawidłowo analizować kod, który sprawia, że intensywnie korzysta z nich. Gdy analizator tagów napotka nieznaną konstrukcję kodu, może pominąć cały region kodu.

Istnieją dwa typowe sposoby, w których ten manifest występuje w programie Visual Studio:

1. Jeśli na pasku nawigacyjnym jest wyświetlane wewnętrzne makro, bieżąca definicja funkcji została pominięta:

   ![Analizator tagów pomija definicję funkcji](media/vcpp-intellisense-tag-parser-macro.png)

1. Środowisko IDE oferuje do tworzenia definicji funkcji dla funkcji, która jest już zdefiniowana:

   ![Analizator tagów oferuje do definiowania istniejącej funkcji](media/vcpp-intellisense-tag-parser-function.png)

Aby rozwiązać ten problem, Dodaj plik o nazwie **cpp. Hint** do katalogu głównego katalogu rozwiązania. Aby uzyskać więcej informacji, zobacz [pliki podpowiedzi](/cpp/build/reference/hint-files).

Błędy analizatora tagów pojawiają się w oknie **Lista błędów** .

## <a name="validate-project-settings-with-diagnostic-logging"></a>Weryfikowanie ustawień projektu przy użyciu rejestrowania diagnostycznego

Aby sprawdzić, czy kompilator IntelliSense korzysta z poprawnych opcji kompilatora, w tym do dołączania do nich i makr preprocesora, Włącz rejestrowanie diagnostyczne wierszy poleceń IntelliSense w **narzędziu > opcjeC++ > edytorze tekstów > C/> Advanced > Rejestrowanie diagnostyczne**. Ustaw opcję **Włącz rejestrowanie** na wartość true, **poziom rejestrowania** na 5 (największa pełna) i **Filtr rejestrowania** na 8 (rejestrowanie IntelliSense).

Okno Dane wyjściowe będzie teraz wyświetlał wiersze poleceń, które są przesyłane do kompilatora IntelliSense. Oto przykładowe dane wyjściowe:

```output
 [IntelliSense] Configuration Name: Debug|Win32
 [IntelliSense] Toolset IntelliSense Identifier:
 [IntelliSense] command line options:
 /c
 /I.
 /IC:\Repo\Includes
 /DWIN32
 /DDEBUG
 /D_DEBUG
 /Zc:wchar_t-
 /Zc:forScope
 /Yustdafx.h
```

Te informacje mogą ułatwić zrozumienie, dlaczego technologia IntelliSense dostarcza niedokładne informacje. Na przykład, jeśli katalog dołączania projektu zawiera **$ (\Include)** , a dziennik diagnostyczny zawiera **/I\Include** jako ścieżkę dołączania, oznacza to, że **$ (NazwaMojejZmiennej)** nie został oceniony i został usunięty z ostatniej ścieżki dołączania .

## <a name="about-the-intellisense-build"></a>Informacje o kompilacji IntelliSense

Program Visual Studio używa dedykowanego C++ kompilatora, aby utworzyć i zachować bazę danych, która ma uprawnienia do wszystkich funkcji IntelliSense. Aby zachować synchronizację bazy danych IntelliSense z kodem, program Visual Studio automatycznie uruchamia funkcję IntelliSense tylko jako zadania w tle w odpowiedzi na pewne zmiany wprowadzone w ustawieniach projektu lub plikach źródłowych.

Jednak w niektórych przypadkach program Visual Studio może nie aktualizować bazy danych IntelliSense w odpowiednim czasie. Na przykład po uruchomieniu polecenia **narzędzia Git ściągania** lub **git** program Visual Studio może potrwać do godziny w celu wykrycia zmian w plikach. Aby wymusić ponowne skanowanie wszystkich plików w rozwiązaniu, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Skanuj ponownie rozwiązanie**.

## <a name="troubleshooting-intellisense-build-failures"></a>Rozwiązywanie problemów z błędami kompilacji IntelliSense

Kompilacja IntelliSense nie tworzy plików binarnych, ale nadal może się nie powieść. Jedną z możliwych przyczyn niepowodzenia jest Custom. props lub. targets. W programie Visual Studio 2017 w wersji 15,6 lub nowszej, w oknie danych wyjściowych są rejestrowane błędy kompilacji tylko dla technologii IntelliSense. Aby je wyświetlić, ustaw polecenie **Pokaż dane wyjściowe z** do **rozwiązania**:

![Okno dane wyjściowe dla błędów rozwiązania](media/vcpp-intellisense-output-window.png)

Komunikat o błędzie może polecić Włączenie śledzenia czasu projektowania:

```output
 error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
 configuration 'Debug|x64'. IntelliSense might be unavailable.
 Set environment variable TRACEDESIGNTIME=true and restart
 Visual Studio to investigate.
```

W przypadku ustawienia zmiennej środowiskowej środowiskową TRACEDESIGNTIME na true i ponownego uruchomienia programu Visual Studio w katalogu% TEMP% zostanie wyświetlony plik dziennika, który może pomóc zdiagnozować błąd kompilacji.

Aby dowiedzieć się więcej na temat zmiennej środowiskowej środowiskową TRACEDESIGNTIME, zobacz [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) i [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Informacje zawarte w tych artykułach są odpowiednie C++ dla projektów.

## <a name="see-also"></a>Zobacz też

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
