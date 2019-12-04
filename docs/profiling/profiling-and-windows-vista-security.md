---
title: Profilowanie i zabezpieczenia systemu Windows Vista | Microsoft Docs
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2a74862d59fe402cbfd9e6bfa804d62ca4c8310b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778378"
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista

W zależności od [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] ustawień uprawnień dostępu użytkownika dostępnych przez administratora komputera, indywidualni użytkownicy mogą mieć uprawnienia zabezpieczeń do profilowania procesu na tym komputerze. Poniższe przykłady ilustrują ewentualne różnice między użytkownikami:

- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.

- Użytkownicy domeny mogą uzyskać dostęp tylko do profilowania przykładowych.

- Niektórzy użytkownicy mogą odmówić dostępu do profilowania wszystkim innym użytkownikom.

  Aby uzyskać więcej informacji, zobacz Opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilowanie między sesjami

*Profilowanie między sesjami* to możliwość profilowania procesu, który jest uruchamiany w innej sesji użytkownika. Na przykład większość usług jest uruchomionych w sesji 0, a użytkownicy nie mogą być uruchamiani bezpośrednio w sesji 0. Za pomocą przycisku **Dołącz do procesu** na pasku narzędzi Eksplorator wydajności lub opcji `/attach` narzędzia wiersza polecenia VSPerfCmd można profilować większość procesów w różnych sesjach użytkowników.

Listę procesów, które są dostępne, można wyświetlić, ustawiając opcje widoczności profilowania między procesami. Te opcje są dostępne w oknie **Dołącz do procesu** , który jest wyświetlany po wybraniu opcji **Dołącz do procesu**:

- **Pokaż procesy wszystkich użytkowników**

  Gdy ta opcja nie jest zaznaczona, na liście są wyświetlane tylko te procesy, których właścicielem jest bieżący użytkownik. W przeciwnym razie lista wyświetla procesy wszystkich użytkowników.

- **Pokaż procesy we wszystkich sesjach**

  Gdy ta opcja nie jest zaznaczona, na liście są wyświetlane procesy w bieżącej sesji. W przeciwnym razie lista wyświetla procesy we wszystkich sesjach.

## <a name="see-also"></a>Zobacz także

- [Omówienia](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Instrukcje: dołączanie do uruchomionego procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
