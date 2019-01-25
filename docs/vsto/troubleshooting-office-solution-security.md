---
title: Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f2cb978ddd62c3e274133e2d209c2634783c708
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871237"
---
# <a name="troubleshoot-office-solution-security"></a>Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office
  Ten temat zawiera wskazówki dotyczące rozwiązywania typowych problemów, które można napotkać podczas pracy z Zabezpieczanie rozwiązań pakietu Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Nie można zainstalować zaufanymi rozwiązaniami z witryny z ograniczeniami  
 Użytkownicy nie mogą instalować to rozwiązanie z lokalizacji w sieci web, jeśli witryna sieci Web znajduje się w programie Internet Explorer strefy witryn z ograniczeniami. Ta zasada obowiązuje, nawet wtedy, gdy rozwiązanie jest podpisany przy użyciu zaufanego certyfikatu.  
  
 Adres URL pliku manifestu wdrożenia można podzielić na jednej z pięciu stref:  
  
- Mój komputer  
  
- Internet  
  
- Lokalny intranet  
  
- Zaufane witryny  
  
- Witryn z ograniczeniami  
  
  Jeśli lokalizacja pliku manifestu wdrożenia zostało przypisane do strefy witryn z ograniczeniami [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie można zainstalować rozwiązania. Jeśli lokalizacja jest znana i może być za zaufany, użytkownik może usunąć lokalizację ze strefy witryn z ograniczeniami i zainstalować rozwiązanie. Aby dowiedzieć się, jak zarządzać strefami, zobacz [Konfigurowanie ClickOnce zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Nie można zainstalować rozwiązania z udziałów plików sieciowych lub lokalizacje w sieci web, po zainstalowaniu Konfiguracja zwiększonych zabezpieczeń programu Internet Explorer lub Internet Explorer 7  
 Internet Explorer zwiększonych zabezpieczeń konfiguracji (IEESC) w systemie Windows Server 2003 lub nowszym i Internet Explorer 7 lub nowszy, znacznie ogranicza możliwość przeglądania Internetu przez użytkowników. Gdy użytkownicy próbują zainstalować Udostępnianie rozwiązań pakietu Office z pliku sieciowego lub lokalizacji w sieci web, może być otrzymują następujący komunikat o błędzie: "Niestandardowe funkcje w tej aplikacji nie będą działać, ponieważ certyfikat używany do podpisywania manifestu wdrażania *SolutionName* nie jest zaufany. Skontaktuj się z administratorem, aby uzyskać dalszą pomoc."  
  
 IEESC i Internet Explorer 7 lub nowszy Jeśli adres URL manifestu wdrażania jest dzielony na kategorie w strefie Internet, manifestu musi mieć certyfikat od zaufanego wydawcy lub nie można zainstalować rozwiązania. Bez IEESC zachowanie domyślne jest na monitowanie użytkownika końcowego do podjęcia decyzji o zaufaniu.  
  
 Aby zarządzanie efekt IEESC i Internet Explorer 7 i nowszym, identyfikowanie witryn sieci Web i universal naming convention (UNC) ścieżki, zaufania i dodać je do jednej ze stref zabezpieczeń zaufanych (Lokalny intranet lub Zaufane witryny). Aby dowiedzieć się, jak zarządzać strefami, zobacz [ClickOnce Konfigurowanie zaufanych wydawców](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)  
