---
title: Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 8c43c48a797619f86f81e219e31ccf2afab5ba87
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279312"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense

W niektórych przypadkach może być konieczne ręczne skonfigurowanie projektu języka C++, aby program IntelliSense działał poprawnie. W przypadku projektów MSBuild (opartych na plikach .vcxproj) można dostosować ustawienia we właściwościach projektu. W przypadku projektów innych niż MSBuild można dostosować ustawienia w pliku CppProperties.json w katalogu głównym projektu. W niektórych przypadkach może być konieczne utworzenie pliku podpowiedzi, aby pomóc intellisense zrozumieć definicje makr. Ide programu Visual Studio pomaga zidentyfikować i rozwiązać problemy IntelliSense.

## <a name="single-file-intellisense"></a>IntelliSense z jednym plikiem

Po otwarciu pliku, który nie jest uwzględniony w projekcie, Visual Studio zapewnia niektóre IntelliSense obsługi, ale domyślnie nie są wyświetlane squiggles błędów. Jeśli **pasek nawigacyjny** mówi *różne pliki*, to prawdopodobnie wyjaśnia, dlaczego nie widzisz squiggles błąd pod nieprawidłowym kodem, lub dlaczego makra preprocesora nie jest zdefiniowany.

## <a name="check-the-error-list"></a>Sprawdź listę błędów

Jeśli plik nie jest otwarty w trybie pojedynczego pliku, a program IntelliSense nie działa poprawnie, pierwszym miejscem do sprawdzenia jest okno Lista błędów. Aby wyświetlić wszystkie błędy IntelliSense dla bieżącego pliku źródłowego wraz ze wszystkimi dołączonymi plikami nagłówkowymi, wybierz pozycję **Build + IntelliSense** w rozwijanej listy rozwijanej:

![VC++ IntelliSense na liście błędów](media/vcpp-intellisense-error-list.png)

IntelliSense generuje maksymalnie 1000 błędów. Jeśli w plikach nagłówkowych zawartych przez plik źródłowy występuje ponad 1000 błędów, plik źródłowy pokazuje tylko jeden błąd na samym początku pliku źródłowego.

## <a name="ensure-include-paths-are-correct"></a>Upewnij się, że ścieżki #include są poprawne

### <a name="msbuild-projects"></a>Projekty MSBuild

Jeśli zostanie uruchomione kompilacje poza ide programu Visual Studio, a kompilacje są pomyślne, ale IntelliSense jest niepoprawna, jest możliwe, że wiersz polecenia jest zsynchronizowany z ustawieniami projektu dla jednej lub więcej konfiguracji. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i upewnij się, że wszystkie **ścieżki #include** są poprawne dla bieżącej konfiguracji i platformy. Jeśli ścieżki są identyczne we wszystkich konfiguracjach i platformach, można wybrać **wszystkie konfiguracje** i **wszystkie platformy,** a następnie sprawdzić, czy ścieżki są poprawne.

![VC++ Uwzględnij katalogi](media/vcpp-intellisense-include-paths.png)

Aby wyświetlić bieżące wartości makr kompilacji, takie jak **VC_IncludePath,** wybierz wiersz Uwzględnij katalogi i kliknij rozwijane po prawej stronie. Następnie ** \<** wybierz pozycję Edytuj>i kliknij przycisk **Makra.**

### <a name="makefile-projects"></a>Projekty pliku reguł dla programu make

W przypadku projektów Makefile opartych na szablonie projektu NMake wybierz pozycję **NMake** w lewym okienku, a następnie wybierz pozycję **Uwzględnij ścieżkę wyszukiwania** w kategorii **IntelliSense:**

![Projekt Makefile zawiera ścieżki](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Otwieranie folderu projektów

W przypadku projektów CMake upewnij się, że ścieżki #include są poprawnie określone dla wszystkich konfiguracji w pliku CMakeLists.txt. Inne typy projektów mogą wymagać pliku CppProperties.json. Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu IntelliSense za pomocą pliku CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Upewnij się, że ścieżki są poprawne dla każdej konfiguracji, która jest zdefiniowana w pliku.

Jeśli w pliku CppProperties.json występuje błąd składniowy, intellisense w plikach, których dotyczy problem, będzie niepoprawny. Visual Studio wyświetli błąd w oknie danych wyjściowych.

## <a name="tag-parser-issues"></a>Problemy z analizatorem znaczników

Analizator tagów jest "rozmytym" analizatorem C++, który jest używany do przeglądania i nawigacji. Jest bardzo szybki, ale nie próbuje całkowicie zrozumieć każdą konstrukcję kodu.

Na przykład nie ocenia makr preprocesora i dlatego może niepoprawnie przeanalizować kod, który sprawia, że intensywne korzystanie z nich. Gdy Parser tagów napotka nieznaną konstrukcję kodu, może pominąć cały region kodu.

Istnieją dwa typowe sposoby, w których ten problem manifestuje w programie Visual Studio:

1. Jeśli na pasku nawigacyjnym jest wyświetlane najbardziej wewnętrzne makro, bieżąca definicja funkcji została pominięta:

   ![Analizator znaczników pomija definicję funkcji](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE oferuje utworzenie definicji funkcji dla funkcji, która jest już zdefiniowana:

   ![Analizator znaczników oferuje zdefiniowanie istniejącej funkcji](media/vcpp-intellisense-tag-parser-function.png)

Aby rozwiązać tego rodzaju problemy, dodaj plik o nazwie **cpp.hint** do katalogu głównego rozwiązania. Aby uzyskać więcej informacji, zobacz [Pliki podpowiedzi](/cpp/build/reference/hint-files).

Błędy analizatora znaczników są wyświetlane w oknie **Lista błędów.**

## <a name="validate-project-settings-with-diagnostic-logging"></a>Sprawdzanie poprawności ustawień projektu za pomocą rejestrowania diagnostycznego

Aby sprawdzić, czy kompilator IntelliSense używa poprawnych opcji kompilatora, w tym uwzględnij ścieżki i makra preprocesora, włącz rejestrowanie diagnostyczne wierszy poleceń IntelliSense w **obszarze Narzędzia > Opcje > Edytor tekstu > C/C++ > Zaawansowane rejestrowanie diagnostyczne >**. Ustaw **włącz rejestrowanie** na true, **poziom rejestrowania** do 5 (większość pełne) i **Filtr rejestrowania** do 8 (rejestrowanie IntelliSense).

Okno dane wyjściowe będzie teraz wyświetlać wiersze poleceń, które są przekazywane do kompilatora IntelliSense. Oto przykładowe dane wyjściowe:

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

Te informacje mogą pomóc w zrozumieniu, dlaczego intellisense dostarcza niedokładnych informacji. Na przykład jeśli katalog include projektu zawiera **$(MyVariable)\Include**, a dziennik diagnostyczny pokazuje **/I\Include** jako ścieżkę Dołącz, oznacza to, że **$(MyVariable)** nie został oceniony i został usunięty z ostatecznej ścieżki dołączania.

## <a name="about-the-intellisense-build"></a>Informacje o kompilacji IntelliSense

Visual Studio używa dedykowanego kompilatora Języka C++ do tworzenia i obsługi bazy danych, która zasila wszystkie funkcje IntelliSense. Aby zachować zsynchronizowanie bazy danych IntelliSense z kodem, program Visual Studio automatycznie uruchamia kompilacje tylko intellisense jako zadania w tle w odpowiedzi na pewne zmiany wprowadzone w ustawieniach projektu lub plikach źródłowych.

Jednak w niektórych przypadkach visual studio może nie zaktualizować bazy danych IntelliSense w odpowiednim czasie. Na przykład po uruchomieniu **polecenia git pull** lub **git checkout,** Visual Studio może potrwać do godziny, aby wykryć zmiany w plikach. Ponowne wyświetlanie wszystkich plików w rozwiązaniu można wymusić, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierając opcję **Rescan Solution**.

## <a name="troubleshooting-intellisense-build-failures"></a>Rozwiązywanie problemów z błędami kompilacji IntelliSense

Kompilacja IntelliSense nie generuje plików binarnych, ale nadal może zakończyć się niepowodzeniem. Jedną z możliwych przyczyn awarii są niestandardowe pliki .props lub .targets. W programie Visual Studio 2017 w wersji 15.6 i nowszych błędy kompilacji tylko intellisense są rejestrowane w oknie danych wyjściowych. Aby je zobaczyć, ustaw **pokaż dane wyjściowe z** do **rozwiązania:**

![Okno danych wyjściowych dla błędów rozwiązania](media/vcpp-intellisense-output-window.png)

Komunikat o błędzie może poinstruować, aby włączyć śledzenie czasu projektowania:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Jeśli ustawisz zmienną środowiskową TRACEDESIGNTIME na true i ponownie uruchomisz program Visual Studio, zobaczysz plik dziennika w katalogu %TEMP%, co może pomóc w zdiagnozowaniu błędu kompilacji.

Aby dowiedzieć się więcej o zmiennej środowiskowej TRACEDESIGNTIME, zobacz [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) i [Wspólny system projektów](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Informacje zawarte w tych artykułach są istotne dla projektów w języku C++.

## <a name="see-also"></a>Zobacz też

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
