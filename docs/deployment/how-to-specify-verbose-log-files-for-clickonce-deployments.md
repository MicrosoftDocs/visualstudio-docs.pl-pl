---
title: Jak określić pełne pliki dziennika dla wdrożeń ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 1e1d2ca7c58d7da85ad67e56eae7713e517a1d2c
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381772"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Instrukcje: Określanie pełnych plików dziennika dla wdrożeń ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki zawierają szczegółowe informacje dotyczące instalowania, inicjowania, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby zwiększyć szczegóły, które [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisuje w tych plikach dziennika, użyj Edytora rejestru (*regedit.exe*), aby określić poziom szczegółowości.

> [!CAUTION]
> Jeśli używasz edytora rejestru nieprawidłowo, może to spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Korzystanie z edytora rejestru na własne ryzyko.

 Poniższa procedura opisuje sposób określania poziomu szczegółowości dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików dziennika bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.

### <a name="to-specify-verbose-log-files"></a>Aby określić pełne pliki dziennika

1. Otwórz *Regedit.exe*.

2. Przejdź do węzła **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment**.

3. W razie potrzeby utwórz nową wartość ciągu o nazwie `LogVerbosityLevel` .

4. Ustaw `LogVerbosityLevel` wartość na `1` .

## <a name="see-also"></a>Zobacz też
- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)