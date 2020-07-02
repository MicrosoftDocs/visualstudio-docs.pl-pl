---
title: Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office
ms.date: 02/02/2017
ms.topic: troubleshooting
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
ms.openlocfilehash: 76cd454cd66e31db8c521d71183aa479da1fe2a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537413"
---
# <a name="troubleshoot-office-solution-security"></a>Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office
  Ten temat zawiera wskazówki dotyczące rozwiązywania typowych problemów, które mogą wystąpić podczas pracy z zabezpieczaniem rozwiązań pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Nie można zainstalować zaufanych rozwiązań z witryn z ograniczeniami
 Użytkownicy nie mogą instalować rozwiązania z lokalizacji w sieci Web, jeśli witryna sieci Web znajduje się na liście strefy witryn z ograniczeniami programu Internet Explorer. Jest to prawdziwe, nawet jeśli rozwiązanie jest podpisane przy użyciu zaufanego certyfikatu.

 Adres URL manifestu wdrożenia można podzielić na jedną z pięciu stref:

- Mój komputer

- Internet

- Lokalny intranet

- Zaufane witryny

- Witryny z ograniczeniami

  Jeśli lokalizacja manifestu wdrożenia została przypisana do strefy witryn z ograniczeniami, program nie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstaluje tego rozwiązania. Jeśli lokalizacja jest znana i może być zaufana, użytkownik może usunąć lokalizację ze strefy witryn z ograniczeniami i zainstalować rozwiązanie. Informacje o sposobach zarządzania strefami znajdują się w temacie [Konfigurowanie zaufanych wydawców ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Nie można instalować rozwiązań z sieciowych udziałów plików lub lokalizacji sieci Web, gdy jest zainstalowana Konfiguracja zwiększonych zabezpieczeń programu Internet Explorer lub program Internet Explorer 7
 Konfiguracja zwiększonych zabezpieczeń programu Internet Explorer (IEESC) w systemie Windows Server 2003 lub nowszym oraz Internet Explorer 7 lub nowszym znacznie ogranicza możliwość przeglądania Internetu przez użytkowników. Gdy użytkownicy próbują zainstalować rozwiązania pakietu Office z sieciowego udziału plików lub lokalizacji sieci Web, może zostać wyświetlony następujący komunikat o błędzie: "funkcje dostosowane w tej aplikacji nie będą działać, ponieważ certyfikat użyty do podpisania manifestu wdrożenia dla *rozwiązania* nie jest zaufany. Skontaktuj się z administratorem, aby uzyskać dalszą pomoc ".

 W przypadku IEESC i programu Internet Explorer 7 lub nowszego, jeśli adres URL manifestu wdrożenia zostanie skategoryzowany w strefie Internet, manifest musi mieć certyfikat od zaufanego wydawcy lub nie można zainstalować rozwiązania. Bez IEESC, domyślnym zachowaniem jest monitowanie użytkownika końcowego o podjęcie decyzji dotyczącej zaufania.

 Aby zarządzać efektem programu IEESC i Internet Explorer 7 lub nowszego, zidentyfikuj Zaufane witryny sieci Web i ścieżki UNC (Universal Naming Convention), a następnie dodaj je do jednej z zaufanych stref zabezpieczeń (Lokalny intranet lub Zaufane witryny). Informacje o sposobach zarządzania strefami znajdują się w temacie [Konfigurowanie zaufanych wydawców ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
