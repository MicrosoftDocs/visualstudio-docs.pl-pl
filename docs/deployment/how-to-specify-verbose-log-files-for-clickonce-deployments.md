---
title: 'Instrukcje: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c83c31ba8c415de9c2a7be8f60c9c6ee8ba9ac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111535"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Instrukcje: Określanie pełnych plików dziennika dla wdrożeń technologii ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki dokumentu szczegóły dotyczące instalowanie, inicjowanie, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby zwiększyć szczegóły, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisu do tych plików dziennika, użyj Edytora rejestru (*regedit.exe*) można określić poziom szczegółowości.

> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.

 Poniższa procedura opisuje sposób określić poziom szczegółowości dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki dziennika dla bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.

### <a name="to-specify-verbose-log-files"></a>Aby określanie plików pełnego dziennika

1. Otwórz *Regedit.exe*.

2. Przejdź do węzła **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. Jeśli to konieczne, Utwórz nową wartość ciągu o nazwie `LogVerbosityLevel`.

4. Ustaw `LogVerbosityLevel` wartość `1`.

## <a name="see-also"></a>Zobacz także
- [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)