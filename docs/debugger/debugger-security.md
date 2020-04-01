---
title: Zabezpieczenia debugera | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a89e60a47e5bab6580c78275357234bb9d3f1c56
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527926"
---
# <a name="debugger-security"></a>Zabezpieczenia debugera
Możliwość debugowania innego procesu daje bardzo szerokie uprawnienia, które w przeciwnym razie nie mają, zwłaszcza podczas debugowania zdalnie. Złośliwy debuger może wyrządzić rozległe szkody na debugowanym komputerze.

 Jednak wielu deweloperów nie zdaje sobie sprawy, że zagrożenie bezpieczeństwa może również płynąć w przeciwnym kierunku. Jest możliwe dla złośliwego kodu w procesie debugowania, aby zagrozić bezpieczeństwu komputera debugowania: istnieje wiele luk zabezpieczeń, które muszą być chronione przed.

## <a name="security-best-practices"></a>Najlepsze praktyki w zakresie zabezpieczeń
 Istnieje niejawna relacja zaufania między debugowaniem kodu a debugerem. Jeśli chcesz coś debugować, powinieneś być również chętny do jego uruchomienia. Najważniejsze jest to, że musisz być w stanie zaufać, co debugowania. Jeśli nie można ufać, a następnie nie należy debugować go lub należy debugować go z komputera, który można sobie pozwolić na zagrożenie i w odizolowanym środowisku.

 Aby zmniejszyć potencjalną powierzchnię ataku, debugowanie powinno być wyłączone na maszynach produkcyjnych. Z tego samego powodu debugowanie nigdy nie powinny być włączone przez czas nieokreślony.

### <a name="managed-debugging-security"></a>Zarządzane zabezpieczenia debugowania
 Oto kilka ogólnych zaleceń, które mają zastosowanie do wszystkich zarządzanych debugowania.

- Należy zachować ostrożność podczas dołączania do procesu niezaufanego użytkownika: gdy to zrobisz, zakładasz, że jest godny zaufania. Podczas próby dołączenia do procesu niezaufanego użytkownika pojawi się potwierdzenie okna dialogowego z ostrzeżeniem o zabezpieczeniach z pytaniem, czy chcesz dołączyć do procesu. "Zaufani użytkownicy" obejmują użytkownika oraz zestaw standardowych użytkowników powszechnie zdefiniowanych na komputerach z zainstalowanym programem .NET Framework, takimi jak **aspnet,** **localsystem,** **networkservice**i **localservice**. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

- Należy zachować ostrożność podczas pobierania projektu z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Internetu i ładowania go do . Jest to bardzo ryzykowne, aby zrobić nawet bez debugowania. Po wykonaniu tej tej wartości zakładasz, że projekt i kod, który zawiera są godne zaufania.

  Aby uzyskać więcej informacji, zobacz [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md).

### <a name="remote-debugging-security"></a>Zabezpieczenia zdalnego debugowania
 Debugowanie lokalne jest na ogół bezpieczniejsze niż zdalne debugowanie. Zdalne debugowanie zwiększa całkowitą powierzchnię, która może być sondowana.

 Monitor zdalnego debugowania programu Visual Studio (msvsmon.exe) jest używany w zdalnym debugowaniu i istnieje kilka zaleceń dotyczących zabezpieczeń dotyczących jego konfigurowania. Preferowanym sposobem skonfigurowania trybu uwierzytelniania jest uwierzytelnianie systemu Windows, ponieważ tryb braku uwierzytelniania nie jest niebezpieczny.

 ![Okno dialogowe Błąd](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 Korzystając z trybu uwierzytelniania systemu Windows, należy pamiętać, że udzielenie niezaufanego uprawnienia użytkownika do łączenia się z msvsmon jest niebezpieczne, ponieważ użytkownik otrzymuje wszystkie uprawnienia na komputerze obsługującym msvsmon.

 Nie debuguj nieznanego procesu na komputerze zdalnym: istnieją potencjalne luki, które mogą mieć wpływ na komputer z systemem debugera lub które mogą naruszyć msvsmon. Jeśli absolutnie musisz debugować nieznany proces, spróbuj debugować lokalnie i użyj zapory, aby zachować zlokalizowane potencjalne zagrożenia.

 Aby uzyskać informacje dotyczące konfigurowania msvsmon, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#bkmk_setup).

### <a name="web-services-debugging-security"></a>Zabezpieczenia debugowania usług sieci Web
 Bezpieczniej jest debugować lokalnie, ale ponieważ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prawdopodobnie nie masz zainstalowanego na serwerze sieci web, debugowanie lokalne może nie być praktyczne. Ogólnie rzecz biorąc debugowanie usług sieci Web odbywa się zdalnie, z wyjątkiem podczas tworzenia, więc zalecenia dotyczące zabezpieczeń zdalnego debugowania dotyczą również debugowania usług sieci Web. Oto kilka dodatkowych sprawdzonych rozwiązań. Aby uzyskać więcej informacji, zobacz [Debugowanie usług XML w sieci Web](https://msdn.microsoft.com/library/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).

- Nie należy włączać debugowania na serwerze sieci Web, który został naruszony.

- Upewnij się, że serwer sieci Web jest bezpieczny przed debugowaniem. Jeśli nie masz pewności, że jest bezpieczny, nie debuguj go.

- Zachowaj szczególną ostrożność podczas debugowania usługi sieci Web udostępnianej w Internecie.

### <a name="external-components"></a>Komponenty zewnętrzne
 Należy pamiętać o stanie zaufania składników zewnętrznych, z którymi program wchodzi w interakcję, zwłaszcza jeśli nie napisałeś kodu. Należy również pamiętać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o składników, które lub debuger może używać.

### <a name="symbols-and-source-code"></a>Symbole i kod źródłowy
 Dwa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia, które wymagają myślenia o bezpieczeństwie są następujące:

- Serwer źródłowy, który udostępnia wersje kodu źródłowego z repozytorium kodu źródłowego. Jest to przydatne, gdy nie masz bieżącej wersji kodu źródłowego programu. [Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufane polecenie](../debugger/security-warning-debugger-must-execute-untrusted-command.md).

- Symbol Server, który jest używany do dostarczania symboli potrzebnych do debugowania awarii podczas wywołania systemowego.

  Zobacz [Określanie symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Zobacz też
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Ostrzeżenie o zabezpieczeniach: Debuger musi wykonać niezaufane polecenie](../debugger/security-warning-debugger-must-execute-untrusted-command.md)