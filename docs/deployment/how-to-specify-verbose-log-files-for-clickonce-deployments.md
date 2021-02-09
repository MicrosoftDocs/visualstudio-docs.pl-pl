---
title: Określ pełne pliki dziennika (wdrożenia ClickOnce)
description: Dowiedz się, jak określić szczegółowość dzienników aktywności, które są obsługiwane przez ClickOnce na potrzeby instalowania, inicjowania, aktualizowania i odinstalowywania wdrożenia technologii ClickOnce.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7adb711c77f4bb2dead3190d40065e148760b034
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887474"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Instrukcje: Określanie pełnych plików dziennika dla wdrożeń ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki zawierają szczegółowe informacje dotyczące instalowania, inicjowania, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby zwiększyć szczegóły, które [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapisuje w tych plikach dziennika, użyj Edytora rejestru (*regedit.exe*), aby określić poziom szczegółowości.

> [!CAUTION]
> Jeśli używasz edytora rejestru nieprawidłowo, może to spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Korzystanie z edytora rejestru na własne ryzyko.

 Poniższa procedura opisuje sposób określania poziomu szczegółowości dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików dziennika bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.

### <a name="to-specify-verbose-log-files"></a>Aby określić pełne pliki dziennika

1. Otwórz *Regedit.exe*.

2. Przejdź do węzła **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.

3. W razie potrzeby utwórz nową wartość ciągu o nazwie `LogVerbosityLevel` .

4. Ustaw `LogVerbosityLevel` wartość na `1` .

## <a name="see-also"></a>Zobacz też
- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)