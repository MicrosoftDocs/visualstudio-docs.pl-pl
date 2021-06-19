---
title: Diagnostyka grafiki | Microsoft Docs
description: Visual Studio Diagnostyka grafiki to zestaw narzędzi do rejestrowania i analizowania działań Direct3D. Użyj ich do rozwiązywania problemów z renderowaniem i wydajnością.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6b769131831a0f1f94aa4fcc8e94a9a88bf9890
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386127"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki w programie Visual Studio
>[!NOTE]
> Visual Studio PIX w systemie Windows dla gier DirectX 12. [PIX w systemie Windows](https://aka.ms/PIXonWindows) to narzędzie do dostrajania i debugowania wydajności, które w pełni obsługuje technologię DirectX 12. [Dowiedz się więcej lub pobierz](visual-studio-graphics-diagnostics-directx-12.md) [tutaj](https://aka.ms/downloadPIX).

Visual Studio *Diagnostyka grafiki* to zestaw narzędzi do rejestrowania, a następnie analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Diagnostyka grafiki można używać w aplikacjach działających lokalnie na komputerze z systemem Windows, w emulatorze urządzenia z systemem Windows lub na zdalnym komputerze lub urządzeniu.

 Przepływ pracy Diagnostyka grafiki rozpoczyna się od przechwytowania rekordu sposobu, w jaki aplikacja korzysta z direct3D — na żywo podczas jego działania — tak aby jego zachowanie można było natychmiast analizować, udostępniać lub zapisywać do późniejszego zapisania. Sesje przechwytywania można inicjować i kontrolować ręcznie z Visual Studio lub za pomocą narzędzia do przechwytywania wiersza **poleceniadxcap.exe**. Sesje przechwytywania można również inicjować i kontrolować programowo przy użyciu interfejsów API Diagnostyka grafiki przechwytywania.

 Po nagraniu sesji przechwytywania jej zawartość może być odtwarzana przez analizator grafiki usługi Visual Studio w dowolnym momencie, ponownie tworzyć przechwycone ramki przy użyciu dokładnie tych samych zasobów i poleceń renderowania używanych przez aplikację.  Następnie przy użyciu narzędzi dostępnych w oknie Analizator grafiki można szczegółowo przeanalizować dowolną przechwyconą ramek. Te narzędzia mogą służyć do badania dowolnego wywołania interfejsu API Direct3D, zasobu, obiektu stanu potoku, etapu potoku, a nawet pełnej historii dowolnego piksela w przechwyconej ramce. Korzystając z tych narzędzi razem, można intuicyjnie zbadać problem z renderowaniem, zaczynając od tego, jak pojawia się on w przechwyconej ramce, po przechodzenie do jego głównej przyczyny w kodzie źródłowym aplikacji, programach do cieniowania lub grafikach.

 Aby zdiagnozować problemy z wydajnością, przechwyconą ramkę można przeanalizować przy użyciu narzędzia *do analizy ramek.* To narzędzie bada potencjalne optymalizacje wydajności, automatycznie zmieniając sposób, w jaki aplikacja korzysta z direct3D i testów porównawczych wszystkich odmian. W przeszłości można było ręcznie wprowadzać i testować tego rodzaju zmiany, aby dowiedzieć się, które z nich wywęszły różnicę. W przypadku analizy ramek wystarczy wprowadzić zmiany, które będą się opłacać.

 Diagnostyka grafiki graficznego wyglądu i działania aplikacji Direct3D rozbudowanych graficznie.

 Przejdź do [tematu Przegląd,](overview-of-visual-studio-graphics-diagnostics.md) aby dowiedzieć się więcej na temat Visual Studio Diagnostyka grafiki ofert.

## <a name="in-this-section"></a>W tej sekcji
 [Omówienie](overview-of-visual-studio-graphics-diagnostics.md) Wprowadzenie do Diagnostyka grafiki przepływu pracy i narzędzi.

 [Wprowadzenie](getting-started-with-visual-studio-graphics-diagnostics.md) W tej sekcji dowiesz się, jak zainstalować aplikację Visual Studio Diagnostyka grafiki i jak rozpocząć korzystanie Diagnostyka grafiki z aplikacją Direct3D.

 [Przechwytywanie informacji graficznych](capturing-graphics-information.md) Aby użyć Diagnostyka grafiki do zbadania problemu z renderowaniem w aplikacji, należy najpierw zarejestrować informacje o tym, jak aplikacja używa directx. Podczas sesji rejestrowania, gdy aplikacja działa normalnie, przechwytywane *są* (czyli wybierane) ramki, które Cię interesują. Przechwycenia zawierają szczegółowe informacje na temat sposobu renderowania ramek. Przechwycone informacje można zapisać jako dokument dziennika grafiki w celu późniejszego zbadania lub udostępnienia innym członkom zespołu.

 [Użycie procesora GPU](../../profiling/gpu-usage.md) Aby użyć Diagnostyka grafiki do profilowania aplikacji, użyj narzędzia Użycie procesora GPU. Użycie procesora GPU może być używane razem z innymi narzędziami profilowania, takimi jak użycie procesora CPU, w celu skorelowania aktywności procesora CPU i procesora GPU, które mogą przyczynić się do problemów z wydajnością w aplikacji.

 [Dokument dziennika grafiki](graphics-log-document.md) Aby rozpocząć badanie zarejestrowanego dziennika grafiki, należy użyć okna dokument dziennika grafiki, aby wybrać przechwyconą ramkę , a nawet określony piksel, aby można było szczegółowo zbadać zdarzenia *(czyli* wywołania interfejsu API DirectX), które mają na nie wpływ.

 [Analiza ramek](graphics-frame-analysis.md) Po wybraniu ramki użyj opcji analiza klatek grafiki, aby sprawdzić i dostroić wydajność renderowania.

 [Lista zdarzeń](graphics-event-list.md) Po wybraniu ramki należy użyć  listy zdarzeń grafiki do zbadania jej zdarzeń w celu określenia, czy są one związane z problemem z renderowaniem.

 [Stan](graphics-state.md) Okno Stan pomaga zrozumieć stan grafiki, który jest aktywny w czasie bieżącego zdarzenia.

 [Etapy potoku](graphics-pipeline-stages.md) W **oknie Etapy potoku** grafiki zbadasz, jak aktualnie wybrane zdarzenie jest przetwarzane przez każdy etap potoku grafiki, aby określić, gdzie najpierw pojawia się problem z renderowaniem. Badanie etapów potoku jest szczególnie przydatne, gdy obiekt nie pojawia się z powodu nieprawidłowego przekształcenia lub gdy jeden z etapów generuje dane wyjściowe, które nie są zgodne z oczekiwaniami następnego etapu.

 [Stos wywołań zdarzeń](graphics-event-call-stack.md) Stos wywołań zdarzeń grafiki **umożliwia** badanie stosu wywołań aktualnie wybranego zdarzenia, dzięki czemu można przejść do kodu aplikacji powiązanego z problemem z renderowaniem.

 [Historia pikseli](graphics-pixel-history.md) Korzystając z okna **Historia pikseli** grafiki do analizowania wpływu zdarzeń, które miały na niego wpływ na aktualnie wybrany piksel, można zidentyfikować zdarzenie lub kombinację zdarzeń, które powodują pewne rodzaje problemów z renderowaniem. Historia pikseli jest szczególnie przydatna, gdy obiekt jest renderowany niepoprawnie, ponieważ dane wyjściowe modułu cieniowania pikseli są nieprawidłowe lub zostały niepoprawnie połączone z buforem ramowym lub gdy obiekt nawet nie jest wyświetlany, ponieważ jego piksele zostały odrzucone przed dotarciem do buforu ramki.

 [Tabela obiektów](graphics-object-table.md) Tabela obiektów **graficznych** umożliwia badanie właściwości i zawartości określonych obiektów Direct3D i zasobów, które są w mocy dla aktualnie wybranego zdarzenia. Tabela obiektów może pomóc w ustaleniu kontekstu urządzenia graficznego, który jest aktywny podczas zdarzenia, i zbadaniu zawartości zasobów graficznych, takich jak stałe bufory, bufory wierzchołków i tekstury.

 [Debuger HLSL](hlsl-shader-debugger.md) Aby sprawdzić, jak zachowuje się kod cieniowania dla aktualnie wybranego zdarzenia i etapu potoku grafiki, użyj **debugera HLSL,** aby przejść przez kod, zbadać zawartość zmiennych i wykonać inne typowe zadania debugowania. Możesz również użyć debugera HLSL, aby zbadać kod cieniowania obliczeń, niezależnie od tego, czy wyniki są dalej przetwarzane przez potok grafiki, czy po prostu odczytywane przez aplikację.

 [Narzędzie przechwytywania wiersza polecenia](command-line-capture-tool.md) Narzędzie przechwytywania wiersza polecenia umożliwia szybkie przechwytywanie i odtwarzanie informacji graficznych bez Visual Studio przechwytywania programowego. W szczególności można użyć narzędzia przechwytywania wiersza polecenia do automatyzacji lub w środowisku testowym.

 [Przykłady](graphics-diagnostics-examples.md) Kilka przykładów pokazuje, jak używać narzędzi Diagnostyka grafiki do diagnozowania różnych rodzajów problemów z renderowaniem.

## <a name="related-sections"></a>Sekcje pokrewne

| Tytuł | Opis |
| - | - |
| [Przewodnik po funkcji debugera](../debugger-feature-tour.md) | Wprowadzono funkcje debugowania w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| [Grafika i gry DirectX](/windows/win32/directx) | Zawiera artykuły, w których omówiono technologie graficzne DirectX. |
| [Obsługa DirectX 12 w Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | Dowiedz się więcej na temat obsługi directx 12 w Visual Studio |
