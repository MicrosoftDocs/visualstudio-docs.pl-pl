---
title: Ustawianie niestandardowej lokalizacji pliku dziennika (błędy wdrażania ClickOnce)
description: Dowiedz się więcej na temat plików dziennika aktywacji, które są obsługiwane przez ClickOnce dla wszystkich wdrożeń, które dokumentują błędy instalacji i inicjowania wdrożenia technologii ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e527e1aec630faadec6e594f944a6715028c6d82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885056"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Instrukcje: ustawienie niestandardowej lokalizacji pliku dziennika dla błędów wdrażania ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przechowuje pliki dziennika aktywacji dla wszystkich wdrożeń. Rejestruje wszystkie błędy związane z instalacją i inicjalizacją [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzy jeden plik dziennika dla każdej aktywacji wdrożenia. Te pliki dzienników są przechowywane w folderze tymczasowych plików internetowych. Plik dziennika wdrożenia jest wyświetlany użytkownikowi, gdy wystąpi awaria aktywacji, a użytkownik klika **szczegóły** w oknie dialogowym błędu.

 Można zmienić to zachowanie dla określonego klienta przy użyciu Edytora rejestru (**regedit.exe**), aby ustawić niestandardową ścieżkę do pliku dziennika. W takim przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rejestruje sukcesy i niepowodzenia aktywacji wszystkich wdrożeń w pojedynczym pliku.

> [!CAUTION]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Korzystanie z edytora rejestru na własne ryzyko.

> [!NOTE]
> Należy najpierw obciąć lub usunąć plik dziennika, aby zapobiec jego powiększaniu.

 Poniższa procedura opisuje sposób ustawienia niestandardowej lokalizacji pliku dziennika dla jednego klienta.

### <a name="to-set-a-custom-log-file-location"></a>Aby ustawić niestandardową lokalizację pliku dziennika

1. Otwórz **Regedit.exe**.

2. Przejdź do węzła `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Ustaw wartość ciągu `LogFilePath` na pełną ścieżkę i nazwę pliku preferowanej niestandardowej lokalizacji dziennika.

     Ta lokalizacja musi znajdować się w katalogu, do którego użytkownik ma dostęp do zapisu. Na przykład w systemie Windows Vista Utwórz następującą strukturę folderów i ustaw wartość `LogFilePath` *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Zobacz też
- [Rozwiązywanie problemów z wdrożeniami technologii ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)