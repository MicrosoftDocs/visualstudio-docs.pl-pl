---
title: Ustaw niestandardową lokalizację pliku dziennika dla błędów wdrażania ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05ffd1cf32f8c7ea93e63232f7026c6c926f9308
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382175"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Instrukcje: ustawienie niestandardowej lokalizacji pliku dziennika dla błędów wdrażania ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]przechowuje pliki dziennika aktywacji dla wszystkich wdrożeń. Rejestruje wszystkie błędy związane z instalacją i inicjalizacją [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzy jeden plik dziennika dla każdej aktywacji wdrożenia. Te pliki dzienników są przechowywane w folderze tymczasowych plików internetowych. Plik dziennika wdrożenia jest wyświetlany użytkownikowi, gdy wystąpi awaria aktywacji, a użytkownik klika **szczegóły** w oknie dialogowym błędu.

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