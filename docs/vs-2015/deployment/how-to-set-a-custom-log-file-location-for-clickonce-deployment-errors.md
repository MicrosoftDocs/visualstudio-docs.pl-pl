---
title: 'Instrukcje: Ustawienie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: a38e453d9bfff3b2633eb98cc5d6127fa126335f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797813"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Instrukcje: Ustawianie niestandardowej lokalizacji pliku dziennika błędów wdrażania technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przechowuje pliki dziennika aktywacji dla wszystkich wdrożeń. Te dzienniki dokumentu wszelkie błędy dotyczące instalowania i Inicjowanie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tworzy jeden plik dziennika dla każdego wdrożenia aktywacji. Przechowuje te pliki dziennika w folderze tymczasowych plików internetowych. Plik dziennika dla wdrożenia jest wyświetlany użytkownikowi, wystąpi błąd aktywacji, gdy użytkownik kliknie **szczegóły** wynikowy w oknie dialogowym błędu.  
  
 To zachowanie można zmienić dla konkretnego klienta, za pomocą Edytora rejestru (**regedit.exe**) można ustawić ścieżki pliku dziennika niestandardowego. W tym przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dzienników aktywacji sukcesów i niepowodzeń dla wszystkich wdrożeń w jednym pliku.  
  
> [!CAUTION]
>  Jeśli korzystanie z Edytora rejestru może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Użyj Edytora rejestru na własne ryzyko.  
  
> [!NOTE]
>  Konieczne będzie obcięcia lub usunąć plik dziennika co pewien czas, aby uniemożliwić zbyt duże.  
  
 Poniższa procedura opisuje sposób ustawiania niestandardowej lokalizacji pliku dziennika dla jednego klienta.  
  
### <a name="to-set-a-custom-log-file-location"></a>Aby ustawić lokalizację pliku dziennika niestandardowego  
  
1.  Otwórz **Regedit.exe**.  
  
2.  Przejdź do węzła `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Ustaw wartość ciągu `LogFilePath` pełną ścieżkę i nazwę pliku dziennika niestandardowego preferowanych lokalizacji.  
  
     Ta lokalizacja musi być w katalogu, do którego użytkownik ma dostęp do zapisu. Na przykład na Windows Vista, utwórz następującą strukturę folderów i ustawić `LogFilePath` do C:\Users\\< nazwa_użytkownika\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
