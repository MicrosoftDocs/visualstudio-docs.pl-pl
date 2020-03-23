---
title: 'Jak: Określ dodatkowe opcje oprzyrządowania | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2d1f7e912ed5960c52e3f0bfa40fe9b87e91a2e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778703"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Instrukcje: określanie dodatkowych opcji instrumentacji

Można instruować pliki binarne z korzystania z programu Visual Studio IDE lub za pomocą narzędzi wiersza polecenia. Jeśli instrumentajne z poziomu IDE, można kontrolować objętość danych, które są zbierane podczas instrumentacji, określając dodatkowe opcje instrumentacji do narzędzia [VSInstr.](../profiling/vsinstr.md) Te opcje są dostępne na poziomie sesji lub na poziomie docelowym. Na przykład, aby uwzględnić lub wykluczyć określone funkcje podczas procesu instrumentacji, użyj opcji dodatkowego instrumentacji na poziomie docelowym.

> [!IMPORTANT]
> Każda wstawiona sonda nieznacznie modyfikuje zachowanie oryginalnego programu. Ta modyfikacja powoduje obciążenie w czasie analizy. Mimo że przybliżenie tego obciążenia jest odejmowane, nadal ma subtelne efekty czasowe dla aplikacji wielowątkowych. Opcje narzędzia [VSInstr](../profiling/vsinstr.md) pomagają kontrolować zbieranie danych podczas profilowania.

## <a name="to-specify-additional-instrumentation-option"></a>Aby określić opcję dodatkowego oprzyrządowania

1. W **Eksploratorze wydajności**wybierz **pozycję Sesja wydajności,** a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

2. Na **stronach Właściwości**kliknij właściwości **Zaawansowane.**

3. Opcje wpisywać w polu **Opcje oprzyrządowania dodatkowe.**

     Na przykład użyj /CONTROL:THREAD, aby określić poziom profilowania. Aby uzyskać pełną listę opcji, zobacz [VSInstr](../profiling/vsinstr.md).

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie](../profiling/configuring-performance-sessions.md)
profilu sesji wydajności[z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
