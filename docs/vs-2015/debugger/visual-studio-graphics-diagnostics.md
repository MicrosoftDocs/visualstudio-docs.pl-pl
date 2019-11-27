---
title: Diagnostyka grafiki programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29ca6b2110038a427c76622d50f769321cda9ff9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296894"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*Diagnostyka grafiki* to zestaw narzędzi do nagrywania, a następnie analizowania problemów z renderowaniem i wydajnością w aplikacjach Direct3D. Diagnostyka grafiki może służyć w aplikacjach, które działają lokalnie na komputerze z systemem Windows, w emulatorze urządzenia Windows lub na zdalnym komputerze lub urządzeniu.  
  
 Diagnostyka grafiki przepływu pracy rozpoczyna się od przechwytywania rekordu w jaki sposób aplikacja używa technologii Direct3D — na żywo, podczas jego wykonywania — tak, aby od razu można analizować swoje zachowanie, udostępnione lub zapisywane do użycia w dalszej części. Sesje przechwytywania można inicjować i kontrolować ręcznie z poziomu programu Visual Studio lub za pomocą narzędzia do przechwytywania wiersza polecenia **DXCap. exe**. Sesje przechwytywania można także inicjować i kontrolować programowo przy użyciu interfejsów API przechwytywania Diagnostyka grafiki.  
  
 Po zarejestrowaniu sesji przechwytywania jej zawartość może zostać odtworzona przez *Analizator grafiki* programu Visual Studio w dowolnym momencie, a następnie ponownie utworzona przechwycone ramki przy użyciu dokładnie tych samych zasobów i poleceń renderowania używanych przez aplikację. Następnie przy użyciu narzędzi dostępnych w oknie Analizator grafiki można analizować wszystkie przechwycone ramki. Te narzędzia można zbadać każde wywołanie interfejsu API Direct3D, zasobów, obiekt stanu potoku, etap potoku lub nawet pełną historię dowolny piksel w przechwyconej ramce. Za pomocą tych narzędzi z optymalizacją, problem z renderowaniem, można eksplorować tylko intuicyjnie, począwszy od sposobu jej wyświetlania w przechwyconej ramce i wyświetlających jego głównej przyczyny problemu w aplikacji źródła kodu, programów do cieniowania lub grafiki zasoby.  
  
 Aby zdiagnozować problemy z wydajnością, przechwyconą ramkę można analizować przy użyciu narzędzia do *analizy klatek* . To narzędzie analizuje potencjalnych optymalizacji wydajności, automatycznie zmienia sposób aplikacja używa technologii Direct3D i testów porównawczych wszystkie odmiany dla Ciebie. W przeszłości, może zostały wprowadzone i ręcznie po prostu badany w tego rodzaju zmian można znaleźć poza te, które wprowadzone różnica. Za pomocą analizy ramek wystarczy wprowadzić zmiany, które już znasz, będzie spłacenie.  
  
 Diagnostyka grafiki pomaga w aplikacji rozbudowanej graficznie Direct3D wyglądają i uruchom doskonale.  
  
 Przejdź do [omówienia](../debugger/overview-of-visual-studio-graphics-diagnostics.md) , aby dowiedzieć się więcej na temat ofert oferowanych przez program Visual Studio Diagnostyka grafiki.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Wprowadza przepływu pracy diagnostyki grafiki i narzędzi.  
  
 [Wprowadzenie](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 W tej sekcji dowiesz się, jak zainstalować program Visual Studio diagnostyki grafiki i jak rozpocząć korzystanie z diagnostyki grafiki z aplikacją Direct3D.  
  
 [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)  
 Aby skorzystać z Graphics Diagnostics, aby zbadać problem z renderowaniem w aplikacji, najpierw zarejestrować informacje o jak aplikacja korzysta z technologii DirectX. Podczas sesji rejestrowania, gdy aplikacja działa normalnie, należy *przechwycić* (czyli zaznaczyć) interesujące Cię ramki. Elementy zawierają szczegółowe informacje na temat sposobu renderowania ramek. Przechwycone informacje można zapisać jako grafiki dokument dziennika, aby sprawdzić później lub udostępnianie innym członkom zespołu.  
  
 [Użycie procesora GPU](../debugger/gpu-usage.md)  
 Aby skorzystać z Graphics Diagnostics do profilu aplikacji, należy użyć narzędzia użycie procesora GPU. Użycie procesora GPU może służyć w połączeniu z innymi narzędziami profilowania, takie jak użycie procesora CPU do skorelowania GPU i CPU działanie, które mogą przyczynić się do problemów z wydajnością w aplikacji.  
  
 [Dokument dziennika grafiki](../debugger/graphics-log-document.md)  
 Aby rozpocząć badanie zarejestrowanego dziennika grafiki, należy użyć okna dokumentu dziennika grafiki do wybrania przechwyconej ramki — lub nawet określonego piksela, aby można było szczegółowo przejrzeć *zdarzenia* (czyli wywołania interfejsu API programu DirectX), które mają na nie wpływ.  
  
 [Analiza ramek](../debugger/graphics-frame-analysis.md)  
 Po zaznaczeniu klatki, należy użyć analiza klatek grafiki do badania i Dostosuj wydajność renderowania.  
  
 [Lista zdarzeń](../debugger/graphics-event-list.md)  
 Po wybraniu ramki należy użyć **listy zdarzeń grafiki** , aby sprawdzić jej zdarzenia w celu ustalenia, czy są one związane z problemem renderowania.  
  
 [Stan](../debugger/graphics-state.md)  
 W oknie stanu ułatwia zrozumienie stanu grafiki, który jest aktywny w momencie bieżącego zdarzenia.  
  
 [Etapy potoku](../debugger/graphics-pipeline-stages.md)  
 W oknie **etapy potoku grafiki** można sprawdzić, w jaki sposób aktualnie wybrane zdarzenie jest przetwarzane przez każdy etap potoku grafiki, aby można było określić, gdzie pojawia się pierwszy problem z renderowaniem. Badanie etapy potoku jest szczególnie przydatne w przypadku, gdy obiekt nie jest wyświetlane ze względu na nieprawidłowe przekształcenie, lub gdy jeden z etapów generuje dane wyjściowe, który nie odpowiada oczekiwaniom kolejnego etapu.  
  
 [Stos wywołań zdarzeń](../debugger/graphics-event-call-stack.md)  
 **Stos wywołań zdarzeń grafiki** służy do badania stosu wywołań aktualnie wybranego zdarzenia, dzięki czemu można przejść do kodu aplikacji, który jest powiązany z problemem renderowania.  
  
 [Historia pikseli](../debugger/graphics-pixel-history.md)  
 Za pomocą okna **Historia pikseli grafiki** , aby przeanalizować sposób, w jaki ma wpływ na bieżące wybrane piksele zdarzeń, które na to wpłynęło, można zidentyfikować zdarzenie lub kombinację zdarzeń, które powodują pewne rodzaje problemów z renderowaniem. Historia pikseli jest szczególnie przydatne w przypadku, gdy obiekt jest renderowany niepoprawnie, ponieważ dane wyjściowe programu do cieniowania pikseli jest niepoprawna lub została połączona niepoprawnie z buforu ramki lub jeśli obiekt nie nawet pojawia się, ponieważ zostały odrzucone pikseli zanim osiągną one buforu ramki.  
  
 [Tabela obiektów](../debugger/graphics-object-table.md)  
 Za pomocą **tabeli obiektów graficznych** można przeanalizować właściwości i zawartość określonych obiektów i zasobów Direct3D, które obowiązują dla aktualnie wybranego zdarzenia. Tabela obiektów może pomóc ustalić kontekst urządzenia grafiki, które są aktywne podczas zdarzenia i sprawdź zawartość zasobów graficznych, takich jak tekstury, stałe bufory i bufory wierzchołków.  
  
 [Debuger HLSL](../debugger/hlsl-shader-debugger.md)  
 Aby sprawdzać, jak zachowuje się kod programu do cieniowania aktualnie wybranego zdarzenia i etapu potoku grafiki, należy użyć **debugera HLSL** , aby przejść do kodu, przejrzeć zawartość zmiennych i wykonać inne typowe zadania debugowania. Debuger HLSL służy również do sprawdzenia kodu cieniowania obliczenia, niezależnie od tego, czy wyniki są dalej przetwarzane przez potok grafiki i po prostu są odczytywane przez aplikację.  
  
 [Narzędzie wiersza polecenia do przechwytywania](../debugger/command-line-capture-tool.md)  
 Narzędzie wiersza polecenia do przechwytywania do szybkiego przechwytywania i odtwarzania informacji graficznych bez korzystania z programu Visual Studio lub przechwytywanie programistyczne. W szczególności można użyć narzędzia wiersza polecenia do przechwytywania, w przypadku usługi automation lub w środowisku testowym.  
  
 [Przykłady](../debugger/graphics-diagnostics-examples.md)  
 Kilka przykładów pokazują, jak za pomocą narzędzi programu Graphics Diagnostics razem diagnozować różne rodzaje problemów z renderowaniem.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Stanowisko|Opis|  
|-----------|-----------------|  
|[Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)|Wprowadza funkcje debugowania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Grafika i gry DirectX](https://go.microsoft.com/fwlink/?LinkId=256498)|Zawiera artykuły na temat technologii grafiki DirectX.|
