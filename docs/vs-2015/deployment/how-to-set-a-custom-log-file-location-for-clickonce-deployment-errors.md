---
title: 'Instrukcje: ustawienie niestandardowej lokalizacji pliku dziennika dla błędów wdrażania ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795942"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Porady: ustawienie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przechowuje pliki dziennika aktywacji dla wszystkich wdrożeń. Rejestruje wszystkie błędy związane z instalacją i inicjalizacją [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Domyślnie program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tworzy jeden plik dziennika dla każdej aktywacji wdrożenia. Te pliki dzienników są przechowywane w folderze tymczasowych plików internetowych. Plik dziennika wdrożenia jest wyświetlany użytkownikowi, gdy wystąpi awaria aktywacji, a użytkownik klika **szczegóły** w oknie dialogowym błędu.  
  
 Można zmienić to zachowanie dla określonego klienta przy użyciu Edytora rejestru (**regedit.exe**), aby ustawić niestandardową ścieżkę do pliku dziennika. W takim przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rejestruje sukcesy i niepowodzenia aktywacji wszystkich wdrożeń w pojedynczym pliku.  
  
> [!CAUTION]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Korzystanie z edytora rejestru na własne ryzyko.  
  
> [!NOTE]
> Należy najpierw obciąć lub usunąć plik dziennika, aby zapobiec jego powiększaniu.  
  
 Poniższa procedura opisuje sposób ustawienia niestandardowej lokalizacji pliku dziennika dla jednego klienta.  
  
### <a name="to-set-a-custom-log-file-location"></a>Aby ustawić niestandardową lokalizację pliku dziennika  
  
1. Otwórz **Regedit.exe**.  
  
2. Przejdź do węzła `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Ustaw wartość ciągu `LogFilePath` na pełną ścieżkę i nazwę pliku preferowanej niestandardowej lokalizacji dziennika.  
  
     Ta lokalizacja musi znajdować się w katalogu, do którego użytkownik ma dostęp do zapisu. Na przykład w systemie Windows Vista Utwórz następującą strukturę folderów i ustaw `LogFilePath` ją na C:\Users \\<username \> \Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
