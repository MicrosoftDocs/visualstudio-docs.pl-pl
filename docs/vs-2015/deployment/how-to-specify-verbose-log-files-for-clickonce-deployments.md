---
title: 'Instrukcje: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441606"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Instrukcje: Określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki dokumentu szczegóły dotyczące instalowanie, inicjowanie, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Aby zwiększyć szczegóły, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapisu do tych plików dziennika, użyj Edytora rejestru (**regedit.exe**) można określić poziom szczegółowości.  
  
> [!CAUTION]
> Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
 Poniższa procedura opisuje sposób określić poziom szczegółowości dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pliki dziennika dla bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.  
  
### <a name="to-specify-verbose-log-files"></a>Aby określanie plików pełnego dziennika  
  
1. Otwórz **Regedit.exe**.  
  
2. Przejdź do węzła `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. Jeśli to konieczne, Utwórz nową wartość ciągu o nazwie `LogVerbosityLevel`.  
  
4. Ustaw `LogVerbosityLevel` wartość `1`.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
