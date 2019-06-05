---
title: Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: fef5f63d8c3fd843ed6f92a313102a9c9879003f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715370"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense

W niektórych przypadkach może być konieczne ręczne skonfigurowanie projektu języka C++ do korzystania z funkcji IntelliSense działa prawidłowo. Dla projektów programu MSBuild (oparte na pliki.vcxproj) można dostosować ustawienia we właściwościach projektu. Dla projektów niekorzystających z programu MSBuild należy dostosować ustawienia w pliku CppProperties.json w katalogu głównym projektu. W niektórych przypadkach może być konieczne utworzenie pliku wskazówki pomagające zrozumieć definicje makr w technologii IntelliSense. Visual Studio IDE ułatwia identyfikowanie i rozwiązywanie problemów IntelliSense.

## <a name="single-file-intellisense"></a>Funkcja IntelliSense pojedynczego pliku

Podczas otwierania pliku, który nie znajduje się w projekcie programu Visual Studio zapewnia obsługę niektórych funkcji IntelliSense, ale domyślnie są wyświetlane nie zygzaki sygnalizujące błędy. Jeśli **pasek nawigacyjny** mówi *różne pliki*, następnie, prawdopodobnie wyjaśnia, dlaczego nie widać zygzaki sygnalizujące błędy w obszarze niepoprawny kod lub dlaczego makro preprocesora nie został zdefiniowany.

## <a name="check-the-error-list"></a>Zapoznaj się z listą błędów

Plik nie jest otwarty w trybie pojedynczego pliku, a funkcja IntelliSense nie działa prawidłowo, pierwsze miejsce, aby sprawdzić, czy okno Lista błędów. Aby zobaczyć wszystkie błędy funkcji IntelliSense dla bieżącego pliku źródłowego oraz wszystkie pliki nagłówkowe uwzględnione, wybierz opcję **kompilacja + IntelliSense** na liście rozwijanej:

![Funkcja IntelliSense VC ++ w liście błędów](media/vcpp-intellisense-error-list.png)

Funkcja IntelliSense daje maksymalnie 1000 błędów. W przypadku ponad 1000 błędów w plikach nagłówkowych dołączane przez plik źródłowy, plik źródłowy zawiera tylko wężyk pojedynczego błędu na samym początku pliku źródłowego.

## <a name="ensure-include-paths-are-correct"></a>Upewnij się, #include ścieżki są poprawne

### <a name="msbuild-projects"></a>Projekty programu MSBuild

Jeśli uruchamianie kompilacji w taki sposób, poza Visual Studio IDE i kompilacje powiodły się, ale technologia IntelliSense jest niepoprawny, to możliwe, że w wierszu polecenia jest zsynchronizowany z ustawienia projektu dla co najmniej jedna konfiguracja. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i upewnij się, że wszystkie **#include** ścieżki są prawidłowe dla bieżącej konfiguracji i platformy. Jeśli ścieżki są identyczne we wszystkie konfiguracje i platformy, możesz wybrać **wszystkie konfiguracje** i **wszystkich platform** i sprawdź, czy ścieżki są poprawne.

![Katalogi plików nagłówkowych VC ++](media/vcpp-intellisense-include-paths.png)

 Aby wyświetlić bieżące wartości dla makra kompilacji takich jak **VC_IncludePath**, zaznacz wiersz Dołącz katalogi i kliknij listę rozwijaną po prawej stronie. Następnie wybierz  **\<Edytuj >** i kliknij pozycję **makra** przycisku.

### <a name="makefile-projects"></a>Projekty pliku reguł dla programu make

Dla projektów plików reguł programu make, które są oparte na szablonie projektu NMake, wybierz **NMake** w okienku po lewej stronie, a następnie wybierz **ścieżkę wyszukiwania dołączenia** w obszarze **IntelliSense** Kategoria:

![Ścieżki dołączanych plików projektu pliku reguł programu make](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Otwórz Folder projektów

Upewnij się, że w przypadku projektów CMake #include ścieżki są poprawnie określone w przypadku wszystkich konfiguracji w pliku CMakeLists.txt. Inne typy projektów mogą wymagać pliku CppProperties.json. Aby uzyskać więcej informacji, zobacz [skonfigurować funkcję IntelliSense za pomocą CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-intellisense-and-browsing-hints-with-cpppropertiesjson). Upewnij się, że ścieżki są prawidłowe dla każdej konfiguracji, która jest zdefiniowana w pliku.

Jeśli występuje błąd składni w pliku CppProperties.json, funkcja IntelliSense w plikach, których to dotyczy będą nieprawidłowe. Program Visual Studio wyświetli błąd, w oknie danych wyjściowych.

## <a name="tag-parser-issues"></a>Problemy dotyczące analizatora tagu

Analizator znacznika jest "rozmytego" analizatora języka C++, który służy do przeglądania i nawigacji. Jest bardzo szybkie, ale nie jest podejmowana próba całkowicie pojąć przykłady co konstrukcję kodu.

Na przykład go nie szacuje makra preprocesora, a w związku z tym niepoprawnie może przeanalizować kodu, która intensywnie korzysta z nich. Po tagu analizator składni napotka konstrukcja nieznanego kodu, Pomiń ten cały region kodu.

Istnieją dwie typowe sposoby, w których ten problem występuje w programie Visual Studio:

1. Jeśli na pasku nawigacyjnym wskazuje najbardziej makra, bieżącej definicji funkcji zostało pominięte:

   ![Analizator znacznika pomija definicji funkcji](media/vcpp-intellisense-tag-parser-macro.png)

1. Oferuje środowisko IDE do tworzenia definicji funkcji dla funkcji, która jest już zdefiniowany:

   ![Analizator znacznika umożliwia definiowanie istniejącą funkcję](media/vcpp-intellisense-tag-parser-function.png)

Aby rozwiązać tego rodzaju problemy, Dodaj plik o nazwie **cpp.hint** do głównego katalogu rozwiązania. Aby uzyskać więcej informacji, zobacz [pliki wskazówki](/cpp/build/reference/hint-files).

Błędy parsera tagów są wyświetlane w **lista błędów** okna.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Sprawdź poprawność ustawień projektu za pomocą funkcji rejestrowania diagnostycznego

Aby sprawdzić, czy kompilator IntelliSense przy użyciu opcji kompilatora poprawne, w tym ścieżki dołączanych plików i makra preprocesora, Włącz w wierszach polecenia diagnostycznego rejestrowania z technologii IntelliSense w **Narzędzia > Opcje > Edytor tekstu > C/C++ > Zaawansowane > Rejestrowanie diagnostyczne**. Ustaw **Włącz rejestrowanie** na wartość True, **poziomu rejestrowania** do 5 (najbardziej szczegółowy) i **rejestrowanie filtru** do 8 (rejestrowanie funkcji IntelliSense).

W oknie danych wyjściowych będą teraz pokazywać wierszy polecenia, które są przekazywane do kompilatora IntelliSense. Poniżej przedstawiono przykładowe dane wyjściowe:

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

Te informacje mogą pomóc Ci zrozumieć, dlaczego dostarcza nieprawidłowych informacji funkcji IntelliSense. Na przykład, jeśli zawiera katalogu plików dołączonych projektu **\Include $(MyVariable)** i pokazuje dziennik diagnostyczny **/I\Include** jako ścieżkę Include, oznacza to, że **$(MyVariable)** nie zostało ocenione i został usunięty z końcowym ścieżki dołączania.

## <a name="about-the-intellisense-build"></a>Temat kompilacji IntelliSense

Visual Studio używa dedykowanego kompilator języka C++ do tworzenia i obsługi bazy danych, w której działają wszystkie funkcje IntelliSense. Można synchronizować bazy danych IntelliSense z kodem, programu Visual Studio powoduje automatyczne uruchomienie kompilacji tylko do funkcji IntelliSense jako zadania w tle w odpowiedzi na niektóre zmiany wprowadzone w ustawieniach projektu lub pliki źródłowe.

Jednak w niektórych przypadkach program Visual Studio może nie aktualizować bazy danych IntelliSense w odpowiednim czasie. Na przykład po uruchomieniu **ściągnięcia usługi git** lub **git checkout** polecenia programu Visual Studio może potrwać do godziny do wykrywania zmian w plikach. Możesz wymusić ponowne skanowanie wszystkich plików w rozwiązaniu, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając pozycję **Skanuj ponownie rozwiązanie**.

## <a name="troubleshooting-intellisense-build-failures"></a>Rozwiązywanie problemów z błędami kompilacji IntelliSense

Kompilacja funkcji IntelliSense nie generuje pliki binarne, ale mogą w dalszym ciągu nie. Jedną z możliwych przyczyn niepowodzenia jest niestandardowe, .props i .targets pliki. W programie Visual Studio 2017 w wersji 15.6 i nowszych błędy kompilacji w trybie tylko do funkcji IntelliSense są rejestrowane w oknie danych wyjściowych. Aby je wyświetlić, należy ustawić **Pokaż dane wyjściowe z** do **rozwiązania**:

![Okno danych wyjściowych dla rozwiązania błędów](media/vcpp-intellisense-output-window.png)

Komunikat o błędzie może wydać polecenie włączenia śledzenia czasu projektowania:

```output
 error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
 configuration 'Debug|x64'. IntelliSense might be unavailable.
 Set environment variable TRACEDESIGNTIME=true and restart
 Visual Studio to investigate.
```

Możesz ustawić zmienną środowiskową TRACEDESIGNTIME na wartość true, a następnie ponownie uruchom program Visual Studio, zobaczysz plik dziennika w katalogu % TEMP %, która może ułatwić diagnozowanie błędów kompilacji.

Aby dowiedzieć się więcej na temat zmienną środowiskową TRACEDESIGNTIME, zobacz [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) i [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Informacje w następujących artykułach są istotne dla projektów w języku C++.

## <a name="see-also"></a>Zobacz też

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
