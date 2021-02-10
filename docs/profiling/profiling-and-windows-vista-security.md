---
title: Profilowanie i zabezpieczenia systemu Windows Vista | Microsoft Docs
description: W zależności od dostępnych ustawień uprawnień dostępu użytkownika każdy użytkownik może mieć uprawnienia zabezpieczeń do profilowania procesu na tym komputerze.
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0419ae09f2b43b396062fc8a3232b0a63c81483c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936395"
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista

W zależności od [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] ustawień uprawnień dostępu użytkownika dostępnych dla administratora komputera każdy użytkownik może mieć uprawnienia zabezpieczeń do profilowania procesu na tym komputerze. Poniższe przykłady ilustrują ewentualne różnice między użytkownikami:

- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawił sterownik i usługę do uruchomienia.

- Użytkownicy domeny mogą uzyskać dostęp tylko do profilowania przykładowych.

- Niektórzy użytkownicy mogą odmówić dostępu do profilowania wszystkim innym użytkownikom.

  Aby uzyskać więcej informacji, zobacz Opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilowanie między sesjami

*Profilowanie między sesjami* to możliwość profilowania procesu, który jest uruchamiany w innej sesji użytkownika. Na przykład większość usług jest uruchomionych w sesji 0, a użytkownicy nie mogą być uruchamiani bezpośrednio w sesji 0. Za pomocą przycisku **Dołącz do procesu** na pasku narzędzi Eksplorator wydajności lub `/attach` opcji narzędzia wiersza polecenia VSPerfCmd można profilować większość procesów w różnych sesjach użytkowników.

Listę procesów, które są dostępne, można wyświetlić, ustawiając opcje widoczności profilowania między procesami. Te opcje są dostępne w oknie **Dołącz do procesu** , który jest wyświetlany po wybraniu opcji **Dołącz do procesu**:

- **Pokaż procesy wszystkich użytkowników**

  Gdy ta opcja nie jest zaznaczona, na liście są wyświetlane tylko te procesy, których właścicielem jest bieżący użytkownik. W przeciwnym razie lista wyświetla procesy wszystkich użytkowników.

- **Pokaż procesy we wszystkich sesjach**

  Gdy ta opcja nie jest zaznaczona, na liście są wyświetlane procesy w bieżącej sesji. W przeciwnym razie lista wyświetla procesy we wszystkich sesjach.

## <a name="see-also"></a>Zobacz też

- [Omówienia](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Instrukcje: dołączanie do uruchomionego procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
