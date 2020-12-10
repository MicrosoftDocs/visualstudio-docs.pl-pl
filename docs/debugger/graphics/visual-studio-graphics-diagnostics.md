---
title: Diagnostyka grafiki | Microsoft Docs
description: Visual Studio Diagnostyka grafiki to zestaw narzędzi do rejestrowania i analizowania aktywności Direct3D. Służą one do rozwiązywania problemów z renderowaniem i wydajnością.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 40b5a8eed74c4ce216e35c391833dcae80fc7efa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994046"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki w programie Visual Studio
>[!NOTE]
> Program Visual Studio zaleca platformy PIX w systemie Windows dla gier DirectX 12. [PIX w systemie Windows](https://aka.ms/PIXonWindows) to narzędzie do dostrajania i debugowania wydajności, które w pełni obsługuje program DirectX 12. [Więcej informacji znajdziesz](visual-studio-graphics-diagnostics-directx-12.md) [tutaj](https://aka.ms/downloadPIX).

Visual Studio *Diagnostyka grafiki* to zestaw narzędzi do nagrywania, a następnie analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Diagnostyka grafiki można używać w aplikacjach, które są uruchamiane lokalnie na komputerze z systemem Windows, w emulatorze urządzenia z systemem Windows lub na komputerze zdalnym lub urządzeniu.

 Przepływ pracy Diagnostyka grafiki rozpoczyna się od przechwytywania rekordu, w jaki sposób aplikacja korzysta z Direct3D — na żywo, tak jak jest uruchomiona, tak aby jej zachowanie można było przeanalizować natychmiast, udostępnić lub zapisać w przyszłości. Sesje przechwytywania można inicjować i kontrolować ręcznie z poziomu programu Visual Studio lub za pomocą narzędzia do przechwytywania wiersza polecenia **dxcap.exe**. Sesje przechwytywania można także inicjować i kontrolować programowo przy użyciu interfejsów API przechwytywania Diagnostyka grafiki.

 Po zarejestrowaniu sesji przechwytywania jej zawartość może zostać odtworzona przez *Analizator grafiki* programu Visual Studio w dowolnym momencie, a następnie ponownie utworzona przechwycone ramki przy użyciu dokładnie tych samych zasobów i poleceń renderowania używanych przez aplikację. Następnie przy użyciu narzędzi dostępnych w oknie Analizator grafiki można analizować wszystkie przechwycone ramki. Te narzędzia mogą służyć do badania dowolnego wywołania interfejsu API Direct3D, zasobu, obiektu stanu potoku, etapu potoku, a nawet pełnej historii dowolnego piksela w przechwyconej ramce. Korzystając z tych narzędzi w ramach uzgodnienia, problem z renderowaniem można zbadać intuicyjnie, rozpoczynając od sposobu jego wyświetlania w przechwyconej ramce i przechodzenia do jego głównej przyczyny w kodzie źródłowym aplikacji, cieniach lub zasobach graficznych.

 Aby zdiagnozować problemy z wydajnością, przechwyconą ramkę można analizować przy użyciu narzędzia do *analizy klatek* . To narzędzie eksploruje potencjalne optymalizacje wydajności przez automatyczne zmianę sposobu, w jaki aplikacja korzysta z Direct3D i przeprowadzania testów porównawczych dla użytkownika. W przeszłości można było wprowadzać i testować ręcznie tego rodzaju zmiany, aby dowiedzieć się, które z nich dokonały różnic. Dzięki analizie klatek wystarczy tylko, że zmiany, które już wiesz, będą obciążane.

 Diagnostyka grafiki pomaga w rozbudowanej i najlepiej funkcjonalnej aplikacji Direct3D.

 Przejdź do [omówienia](overview-of-visual-studio-graphics-diagnostics.md) , aby dowiedzieć się więcej na temat ofert oferowanych przez program Visual Studio Diagnostyka grafiki.

## <a name="in-this-section"></a>W tej sekcji
 [Przegląd](overview-of-visual-studio-graphics-diagnostics.md) Wprowadza Diagnostyka grafiki przepływ pracy i narzędzia.

 [Wprowadzenie](getting-started-with-visual-studio-graphics-diagnostics.md) W tej sekcji dowiesz się, jak zainstalować program Visual Studio Diagnostyka grafiki i jak zacząć korzystać z Diagnostyka grafiki z aplikacją Direct3D.

 [Przechwytywanie informacji graficznych](capturing-graphics-information.md) Aby użyć Diagnostyka grafiki do badania problemu renderowania w aplikacji, należy najpierw zarejestrować informacje o sposobie korzystania z programu DirectX przez aplikację. Podczas sesji rejestrowania, gdy aplikacja działa normalnie, należy *przechwycić* (czyli zaznaczyć) interesujące Cię ramki. Przechwytywanie zawiera szczegółowe informacje o sposobie renderowania ramek. Przechwycone informacje można zapisać jako dokument dziennika grafiki, aby przeanalizować go później lub udostępnić innym członkom zespołu.

 [Użycie procesora GPU](../../profiling/gpu-usage.md) Aby użyć Diagnostyka grafiki do profilowania aplikacji, użyj narzędzia użycie procesora GPU. Użycie procesora GPU może być używane w połączeniu z innymi narzędziami profilowania, takimi jak użycie procesora CPU, w celu skorelowania aktywności procesora i procesora GPU, które mogą przyczynić się do problemów z wydajnością w aplikacji.

 [Dokument dziennika grafiki](graphics-log-document.md) Aby rozpocząć badanie zarejestrowanego dziennika grafiki, należy użyć okna dokumentu dziennika grafiki do wybrania przechwyconej ramki — lub nawet określonego piksela, aby można było szczegółowo przejrzeć *zdarzenia* (czyli wywołania interfejsu API programu DirectX), które mają na nie wpływ.

 [Analiza klatek](graphics-frame-analysis.md) Po wybraniu ramki, użyj analiza klatek grafiki do sprawdzenia i dostrajania wydajności renderowania.

 [Lista zdarzeń](graphics-event-list.md) Po wybraniu ramki należy użyć **listy zdarzeń grafiki** , aby sprawdzić jej zdarzenia w celu ustalenia, czy są one związane z problemem renderowania.

 [Stan](graphics-state.md) Okno stanu pomaga zrozumieć stan grafiki, który jest aktywny w momencie bieżącego zdarzenia.

 [Etapy potoku](graphics-pipeline-stages.md) W oknie **etapy potoku grafiki** można sprawdzić, w jaki sposób aktualnie wybrane zdarzenie jest przetwarzane przez każdy etap potoku grafiki, aby można było określić, gdzie pojawia się pierwszy problem z renderowaniem. Sprawdzanie etapów potoku jest szczególnie przydatne w przypadku, gdy obiekt nie pojawia się z powodu niepoprawnego przekształcenia lub gdy jeden z etapów produkuje dane wyjściowe, które nie są zgodne z oczekiwanym następnym etapem.

 [Stos wywołań zdarzeń](graphics-event-call-stack.md) **Stos wywołań zdarzeń grafiki** służy do badania stosu wywołań aktualnie wybranego zdarzenia, dzięki czemu można przejść do kodu aplikacji, który jest powiązany z problemem renderowania.

 [Historia pikseli](graphics-pixel-history.md) Za pomocą okna **Historia pikseli grafiki** , aby przeanalizować sposób, w jaki ma wpływ na bieżące wybrane piksele zdarzeń, które na to wpłynęło, można zidentyfikować zdarzenie lub kombinację zdarzeń, które powodują pewne rodzaje problemów z renderowaniem. Historia pikseli jest szczególnie przydatna, gdy obiekt jest renderowany nieprawidłowo, ponieważ dane wyjściowe programu do cieniowania pikseli są nieprawidłowe lub nieprawidłowo połączone z buforem ramek albo gdy obiekt nie jest nawet wyświetlany, ponieważ jego piksele zostały odrzucone przed osiągnięciem buforu ramek.

 [Tabela obiektów](graphics-object-table.md) Za pomocą **tabeli obiektów graficznych** można przeanalizować właściwości i zawartość określonych obiektów i zasobów Direct3D, które obowiązują dla aktualnie wybranego zdarzenia. Tabela obiektów może pomóc określić kontekst urządzenia graficznego, który jest aktywny podczas zdarzenia, i sprawdzić zawartość zasobów graficznych, takich jak stałe bufory, bufory wierzchołków i tekstury.

 [Debuger HLSL](hlsl-shader-debugger.md) Aby sprawdzać, jak zachowuje się kod programu do cieniowania aktualnie wybranego zdarzenia i etapu potoku grafiki, należy użyć **debugera HLSL** , aby przejść do kodu, przejrzeć zawartość zmiennych i wykonać inne typowe zadania debugowania. Można również użyć debugera HLSL do zbadania kodu programu do cieniowania obliczeń, bez względu na to, czy wyniki są przetworzone przez potok graficzny, czy po prostu są odczytywane przez aplikację.

 [Narzędzie do przechwytywania wiersza polecenia](command-line-capture-tool.md) Narzędzie do przechwytywania wiersza polecenia umożliwia szybkie przechwytywanie i odtwarzanie informacji graficznych bez użycia programu Visual Studio lub funkcji przechwytywania programowego. W szczególności można użyć narzędzia do przechwytywania wiersza polecenia do automatyzacji lub w środowisku testowym.

 [Przykłady](graphics-diagnostics-examples.md) Kilka przykładów pokazuje, jak za pomocą narzędzi Diagnostyka grafiki narzędzia zdiagnozować różne rodzaje problemów z renderowaniem.

## <a name="related-sections"></a>Sekcje pokrewne

| Tytuł | Opis |
| - | - |
| [Przewodnik po funkcjach debugera](../debugger-feature-tour.md) | Wprowadza funkcje debugowania w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| [Grafika i gry DirectX](/windows/win32/directx) | Zawiera artykuły, które omawiają technologie grafiki DirectX. |
| [Obsługa DirectX 12 w programie Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | Dowiedz się więcej o obsłudze DirectX 12 w programie Visual Studio |
