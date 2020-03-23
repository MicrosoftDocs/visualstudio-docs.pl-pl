---
title: Profilowanie i zabezpieczenia systemu Windows Vista | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778378"
---
# <a name="profiling-and-windows-vista-security"></a>Profilowanie i bezpieczeństwo systemu Windows Vista

W zależności [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] od ustawień uprawnień dostępu użytkownika, które administrator komputera udostępnił, indywidualny użytkownik może mieć uprawnienia zabezpieczeń do profilowania procesu na tym komputerze. Poniższe przykłady ilustrują możliwe różnice między użytkownikami:

- Niektórzy użytkownicy mogą uzyskać dostęp do zaawansowanych funkcji profilowania, gdy administrator ustawi sterownik i usługę do uruchomienia.

- Użytkownicy domeny mogą uzyskać dostęp tylko do przykładowego profilowania.

- Niektórzy użytkownicy mogą odmówić dostępu do profilowania wszystkim innym użytkownikom.

  Aby uzyskać więcej informacji, zobacz opcje ADMIN w [programie VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilowanie między sesyjne

*Profilowanie krzyżowe* to możliwość profilowania procesu, który jest uruchamiany w innej sesji użytkownika. Na przykład większość usług jest uruchamiana w sesji 0, a użytkownicy nie mogą uruchamiać się bezpośrednio w sesji 0. Za pomocą przycisku **Dołącz do procesu** na pasku narzędziOwym Eksploratora wydajności lub `/attach` opcji narzędzia wiersza polecenia VSPerfCmd można profilować większość procesów w różnych sesjach użytkownika.

Listę dostępnych procesów można wyświetlić, ustawiając opcje widoczności profilowania między procesami. Te opcje są dostępne w oknie **Dołącz do procesu,** które jest wyświetlane po wybraniu opcji **Dołącz do procesu:**

- **Pokaż procesy od wszystkich użytkowników**

  Jeśli ta opcja nie jest zaznaczona, na liście są wyświetlane tylko te procesy, które są własnością bieżącego użytkownika. W przeciwnym razie lista wyświetla procesy od wszystkich użytkowników.

- **Pokazywale we wszystkich sesjach**

  Jeśli ta opcja nie jest zaznaczona, na liście są wyświetlane procesy w bieżącej sesji. W przeciwnym razie lista wyświetla procesy we wszystkich sesjach.

## <a name="see-also"></a>Zobacz też

- [Omówienia](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Jak: Dołączanie do uruchomionego procesu](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
