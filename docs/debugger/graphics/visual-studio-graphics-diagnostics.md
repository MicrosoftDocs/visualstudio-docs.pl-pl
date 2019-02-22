---
title: Diagnostyka grafiki | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbc3edfabe041804a632b919eff4e565be9cc5e3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703035"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki w programie Visual Studio
Program Visual Studio*Graphics Diagnostics* to zestaw narzędzi do rejestrowania i następnie analizowania problemów renderowania i wydajności w aplikacjach Direct3D. Diagnostyka grafiki może służyć w aplikacjach, które działają lokalnie na komputerze z systemem Windows, w emulatorze urządzenia Windows lub na zdalnym komputerze lub urządzeniu.

 Diagnostyka grafiki przepływu pracy rozpoczyna się od przechwytywania rekordu w jaki sposób aplikacja używa technologii Direct3D — na żywo, podczas jego wykonywania — tak, aby od razu można analizować swoje zachowanie, udostępnione lub zapisywane do użycia w dalszej części. Sesji przechwytywania, które mogą być zainicjowane i kontrolowane ręcznie z poziomu programu Visual Studio lub za pomocą narzędzia wiersza polecenia do przechwytywania **dxcap.exe**. Można również inicjowane sesji przechwytywania i kontrolowany programowo za pomocą Graphics Diagnostics przechwytywania interfejsów API.

 Po sesji przechwytywania zarejestrowano jego zawartość może zostać odtworzony przez program Visual Studio *analizatora grafiki* w dowolnym momencie i ponowne utworzenie przechwycone ramki przy użyciu dokładnie tych samych zasobów i renderowanie poleceń, aplikacja używana. Następnie przy użyciu narzędzi dostępnych w okno analizator grafiki, dowolny przechwycone ramki mogą być analizowane szczegółowo. Te narzędzia można zbadać każde wywołanie interfejsu API Direct3D, zasobów, obiekt stanu potoku, etap potoku lub nawet pełną historię dowolny piksel w przechwyconej ramce. Za pomocą tych narzędzi z optymalizacją, problem z renderowaniem, można eksplorować tylko intuicyjnie, począwszy od sposobu jej wyświetlania w przechwyconej ramce i wyświetlających jego głównej przyczyny problemu w aplikacji źródła kodu, programów do cieniowania lub grafiki zasoby.

 Aby zdiagnozować problemy z wydajnością, przechwyconej ramki mogą być analizowane za pomocą *analizy klatek* narzędzia. To narzędzie analizuje potencjalnych optymalizacji wydajności, automatycznie zmienia sposób aplikacja używa technologii Direct3D i testów porównawczych wszystkie odmiany dla Ciebie. W przeszłości, może zostały wprowadzone i ręcznie po prostu badany w tego rodzaju zmian można znaleźć poza te, które wprowadzone różnica. Za pomocą analizy ramek wystarczy wprowadzić zmiany, które już znasz, będzie spłacenie.

 Diagnostyka grafiki pomaga w aplikacji rozbudowanej graficznie Direct3D wyglądają i uruchom doskonale.

 W dalszym ciągu [Przegląd](overview-of-visual-studio-graphics-diagnostics.md) dowiedzieć się więcej o co oferuje program Visual Studio diagnostyki grafiki.

## <a name="in-this-section"></a>W tej sekcji
 [Omówienie](overview-of-visual-studio-graphics-diagnostics.md) wprowadza przepływu pracy diagnostyki grafiki i narzędzi.

 [Wprowadzenie do](getting-started-with-visual-studio-graphics-diagnostics.md) w tej sekcji dowiesz się, jak zainstalować program Visual Studio diagnostyki grafiki i jak rozpocząć korzystanie z diagnostyki grafiki z aplikacją Direct3D.

 [Przechwytywanie informacji graficznych](capturing-graphics-information.md) można skorzystać z Graphics Diagnostics, aby zbadać problem z renderowaniem w aplikacji, zapisanie informacji o używaniu aplikacji DirectX. Podczas sesji nagrywania, co aplikacja uruchamia się normalnie, możesz *przechwytywania* (czyli wybierz) ramek, które interesują Cię. Elementy zawierają szczegółowe informacje na temat sposobu renderowania ramek. Przechwycone informacje można zapisać jako grafiki dokument dziennika, aby sprawdzić później lub udostępnianie innym członkom zespołu.

 [Użycie procesora GPU](gpu-usage.md) można skorzystać z Graphics Diagnostics do profilu aplikacji, użyj narzędzia użycie procesora GPU. Użycie procesora GPU może służyć w połączeniu z innymi narzędziami profilowania, takie jak użycie procesora CPU do skorelowania GPU i CPU działanie, które mogą przyczynić się do problemów z wydajnością w aplikacji.

 [Dokument dziennika grafiki](graphics-log-document.md) aby rozpocząć badanie dziennik grafiki zarejestrowane, umożliwia okno dokumentu dziennika grafiki wybierz przechwyconej ramki — a nawet określonych pikseli — tak, aby szczegółowo, można sprawdzić *zdarzenia* (który to wywołania interfejsu API programu DirectX) który wpływa na.

 [Analiza klatek](graphics-frame-analysis.md) po zaznaczeniu klatki, należy użyć analiza klatek grafiki do badania i Dostosuj wydajność renderowania.

 [Lista zdarzeń](graphics-event-list.md) po zaznaczeniu klatki, należy użyć **Lista zdarzeń graficznych** aby zbadać jego zdarzeń, aby ustalić, czy są one związane z problemem renderowania.

 [Stan](graphics-state.md) okna stanu ułatwi Ci zrozumienie stanu grafiki, który jest aktywny w momencie bieżącego zdarzenia.

 [Etapy potoku](graphics-pipeline-stages.md) w **etapy potoku grafiki** okna, Zbadaj, jak aktualnie wybranego zdarzenia jest przetwarzany przez każdy etap potoku grafiki, aby wskazać, gdzie problem z renderowaniem pierwszy zostanie wyświetlone. Badanie etapy potoku jest szczególnie przydatne w przypadku, gdy obiekt nie jest wyświetlane ze względu na nieprawidłowe przekształcenie, lub gdy jeden z etapów generuje dane wyjściowe, który nie odpowiada oczekiwaniom kolejnego etapu.

 [Stos wywołań zdarzenia](graphics-event-call-stack.md) używasz **stos wywołań zdarzenia grafiki** można analizować stos wywołań, które aktualnie wybranego zdarzenia, dzięki czemu można przejść do kodu aplikacji, który jest powiązany z problemem renderowania.

 [Historia pikseli](graphics-pixel-history.md) przy użyciu **Historia pikseli grafiki** okna, aby analizować aktualnie wybrany piksel wpływ zdarzeń, które wpływ, można zidentyfikować zdarzenia lub kombinacji zdarzenia, które powodują pewnych rodzaje problemów z renderowaniem. Historia pikseli jest szczególnie przydatne w przypadku, gdy obiekt jest renderowany niepoprawnie, ponieważ dane wyjściowe programu do cieniowania pikseli jest niepoprawna lub została połączona niepoprawnie z buforu ramki lub jeśli obiekt nie nawet pojawia się, ponieważ zostały odrzucone pikseli zanim osiągną one buforu ramki.

 [Tabela obiektów](graphics-object-table.md) używasz **Graphics Object Table** badało właściwości i zawartość określonego obiektami i zasobami Direct3D, które są stosowane dla aktualnie wybranego zdarzenia. Tabela obiektów może pomóc ustalić kontekst urządzenia grafiki, które są aktywne podczas zdarzenia i sprawdź zawartość zasobów graficznych, takich jak tekstury, stałe bufory i bufory wierzchołków.

 [Debuger HLSL](hlsl-shader-debugger.md) zbadać kod modułu cieniującego dla aktualnie wybranego zdarzenia i grafiki potoku etapu zachowania, należy użyć **Debuger języka HLSL** przejść przez kod, zbadać zawartość zmiennych i wykonywania innych do typowych zadań debugowania. Debuger HLSL służy również do sprawdzenia kodu cieniowania obliczenia, niezależnie od tego, czy wyniki są dalej przetwarzane przez potok grafiki i po prostu są odczytywane przez aplikację.

 [Narzędzie wiersza polecenia przechwytywania](command-line-capture-tool.md) Użyj narzędzia wiersza polecenia do przechwytywania do szybkiego przechwytywania i odtwarzania informacji graficznych bez korzystania z programu Visual Studio lub przechwytywanie programistyczne. W szczególności można użyć narzędzia wiersza polecenia do przechwytywania, w przypadku usługi automation lub w środowisku testowym.

 [Przykłady](graphics-diagnostics-examples.md) kilka przykładów pokazują, jak za pomocą narzędzi programu Graphics Diagnostics razem diagnozować różne rodzaje problemów z renderowaniem.

## <a name="related-sections"></a>Sekcje pokrewne

| Tytuł | Opis |
| - | - |
| [Przewodnik po funkcjach debugera](/visualstudio/debugger/debugger-feature-tour) | Wprowadza funkcji debugowania w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [DirectX Graphics i gry](http://go.microsoft.com/fwlink/?LinkId=256498) | Zawiera artykuły na temat technologii grafiki DirectX. |
