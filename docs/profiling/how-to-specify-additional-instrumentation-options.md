---
title: 'Instrukcje: Określanie dodatkowych opcji Instrumentacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c95add435824663e798d226e0be11ddbe06b8aba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618682"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Instrukcje: Określanie dodatkowych opcji instrumentacji

Możliwe jest instrumentowanie plików binarnych z za pomocą środowiska IDE programu Visual Studio lub za pomocą narzędzia wiersza polecenia. Jeśli Instrumentacji danych binarnych z poziomu środowiska IDE, możesz kontrolować ilość danych zebranych podczas instrumentacji, przez określenie dodatkowych opcji Instrumentacji do [VSInstr](../profiling/vsinstr.md) narzędzia. Te opcje są dostępne na poziomie docelowego lub sesji. Na przykład aby dołączyć lub wykluczyć określone funkcje w procesie instrumentacji, opcja dodatkowe Instrumentacji na poziomie docelowej.

> [!IMPORTANT]
> Każdy sondowania, który jest wstawiany modyfikuje zachowanie oryginalnej programu nieco. Ta modyfikacja spowoduje, że obciążenie w czasie analizy. Mimo że przybliżeniem to obciążenie jest odejmowany, nadal ma skutki subtelne chronometrażu dla aplikacji wielowątkowych. [VSInstr](../profiling/vsinstr.md) narzędzie Pomoc opcji sterowanie zbieraniem danych podczas profilowania.

## <a name="to-specify-additional-instrumentation-option"></a>Aby określić opcję dodatkowe Instrumentacji

1. W **Eksplorator wydajności**, wybierz opcję **sesji wydajności** a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.

2. W **strony właściwości**, kliknij przycisk **zaawansowane** właściwości.

3. Wpisz opcje w **dodatkowych opcji Instrumentacji** pole.

     Na przykład użyć /CONTROL:THREAD, aby określić poziom profilowania. Aby uzyskać pełną listę opcji, zobacz [VSInstr](../profiling/vsinstr.md).

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
[profilu z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)