---
title: Profilowanie i bezpieczeństwo Windows Vista | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 767210a934753dd85b22728813d7608618a2b8d3
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220660"
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista

W zależności od [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] ustawień uprawnień dostępu użytkowników, które udostępnionych przez administratora komputera, użytkownik może być uprawnienia zabezpieczeń do profilowania, proces na tym komputerze. Poniższe przykłady ilustrują możliwe różnice między użytkowników:

- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i uruchomienie usługi.

- Użytkownicy domeny mogą uzyskiwać dostęp do przykładowej profilowanie tylko.

- Niektórzy użytkownicy mogą uniemożliwić dostęp do profilowania, aby wszyscy inni użytkownicy.

  Aby uzyskać więcej informacji, zobacz Opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilowanie między sesjami

*Profilowanie między sesjami* jest możliwość profilować proces uruchomiony w sesji innego użytkownika. Na przykład większość usług uruchamiane w sesji 0, a użytkownicy nie mogą uruchamiać bezpośrednio w sesji 0. Za pomocą **dołączyć do procesu** przycisk na pasku narzędzi Eksploratora wydajności lub `/attach` opcji narzędzia wiersza polecenia narzędzia VSPerfCmd można profilować większość procesów w sesji innego użytkownika.

Można wyświetlić listę procesów, które są dostępne, ustawiając opcje widoczności profilowania między procesami. Te opcje są dostępne w **dołączyć do procesu** okna, który jest wyświetlany po wybraniu **dołączyć do procesu**:

- **Pokaż procesy wszystkich użytkowników**

  Gdy ta opcja nie jest zaznaczona, na liście zostaną wyświetlone tylko procesy, które są własnością bieżącego użytkownika. W przeciwnym razie zostanie wyświetlona lista procesy wszystkich użytkowników.

- **Pokaż procesy we wszystkich sesjach**

  Gdy ta opcja nie jest zaznaczona, zostanie wyświetlona lista procesów w bieżącej sesji. W przeciwnym razie zostanie wyświetlona lista procesy we wszystkich sesjach.

## <a name="see-also"></a>Zobacz także

- [Omówienia](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Porady: dołączanie do uruchomionego procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
