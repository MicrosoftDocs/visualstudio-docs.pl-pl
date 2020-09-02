---
title: 'Instrukcje: Określanie pełnych plików dziennika dla wdrożeń ClickOnce | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64832933"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Porady: określanie plików pełnego dziennika dla wdrożeń technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przechowuje pliki dziennika aktywności dla wszystkich wdrożeń. Te dzienniki zawierają szczegółowe informacje dotyczące instalowania, inicjowania, aktualizowania i odinstalowywania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Aby zwiększyć szczegóły, które [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zapisuje w tych plikach dziennika, użyj Edytora rejestru (**regedit.exe**), aby określić poziom szczegółowości.  
  
> [!CAUTION]
> Jeśli używasz edytora rejestru nieprawidłowo, może to spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Korzystanie z edytora rejestru na własne ryzyko.  
  
 Poniższa procedura opisuje sposób określania poziomu szczegółowości dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] plików dziennika bieżącego użytkownika. Aby zmniejszyć poziom szczegółowości, Usuń tę wartość rejestru.  
  
### <a name="to-specify-verbose-log-files"></a>Aby określić pełne pliki dziennika  
  
1. Otwórz **Regedit.exe**.  
  
2. Przejdź do węzła `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. W razie potrzeby utwórz nową wartość ciągu o nazwie `LogVerbosityLevel` .  
  
4. Ustaw `LogVerbosityLevel` wartość na `1` .  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
