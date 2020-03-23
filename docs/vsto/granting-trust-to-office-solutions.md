---
title: Obdaruj rozwiązaniami pakietu Office zaufaniem
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303303"
---
# <a name="grant-trust-to-office-solutions"></a>Obdaruj rozwiązaniami pakietu Office zaufaniem
  Obdaruj rozwiązaniami pakietu Office o zaufaniu oznacza modyfikowanie zasad zabezpieczeń każdego komputera docelowego w celu zaufania do zestawu rozwiązań, manifestu aplikacji, manifestu wdrażania i dokumentu. Zaufanie może być przyznane rozwiązaniu pakietu Office przez ciebie lub użytkownika końcowego.

 Możesz udzielić pełnego zaufania do rozwiązania pakietu Office, podpisując manifesty aplikacji i wdrażania.

 Użytkownicy końcowi mogą udzielić zaufania do rozwiązania [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pakietu Office, podejmując decyzję o zaufaniu w wierszu zaufania.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Zaufaj rozwiązaniu, podpisując manifesty aplikacji i wdrażania
 Wszystkie manifesty aplikacji i wdrażania dla rozwiązań pakietu Office muszą być podpisane za pomocą certyfikatu identyfikującego wydawcę. Certyfikaty stanowią podstawę do podejmowania decyzji dotyczących zaufania.

 Tymczasowy certyfikat jest tworzony dla Ciebie i przyznane zaufania w czasie kompilacji, więc rozwiązanie zostanie uruchomione podczas debugowania go. Jeśli opublikujesz rozwiązanie podpisane za pomocą certyfikatu tymczasowego, użytkownik końcowy zostanie poproszony o podjęcie decyzji o zaufaniu.

 Jeśli podpiszesz rozwiązanie za pomocą znanego i zaufanego certyfikatu, rozwiązanie zostanie automatycznie zainstalowane bez monitowania użytkownika końcowego o podjęcie decyzji o zaufaniu. Aby uzyskać więcej informacji na temat uzyskiwania certyfikatu do podpisywania, zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md). Po uzyskaniu certyfikatu certyfikat musi być jawnie zaufany, dodając go do listy Zaufani wydawcy. Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Jeśli deweloper podpisze rozwiązanie za pomocą certyfikatu tymczasowego, administrator może ponownie podpisać dostosowanie za pomocą znanego i zaufanego certyfikatu przy użyciu narzędzia do generowania i edytowania manifestu *(mage.exe),* które jest jednym z narzędzi programu Microsoft .NET Framework. Aby uzyskać więcej informacji na temat podpisywania rozwiązań, zobacz [Jak: Podpisywać rozwiązania pakietu Office](../vsto/how-to-sign-office-solutions.md) i [jak: Podpisywać manifesty aplikacji i wdrażania](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Zaufaj rozwiązaniu za pomocą monitu clickonce zaufania
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]monituje użytkownika końcowego do podjęcia decyzji o zaufaniu, jeśli nie ma żadnych zasad dla całej organizacji, która ufa certyfikatowi rozwiązania. Jeśli użytkownik końcowy udziela zaufania do rozwiązania, zostanie utworzony wpis listy dołączania, który zawiera adres URL i klucz publiczny do przechowywania tej decyzji zaufania. Po uruchomieniu zaufanego dostosowania później użytkownik końcowy nie jest ponownie monitowany.

 Administratorzy mogą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] wyłączyć monit zaufania lub wymagać, aby monit występował tylko w przypadku rozwiązań podpisanych za pomocą certyfikatu Authenticode. Aby uzyskać więcej informacji na temat zmiany tych ustawień w strefach MyComputer, LocalIntranet, Internet, TrustedSites i UntrustedSites, zobacz [Jak: Konfigurowanie zachowania monitu zaufania ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Zobacz też

- [Bezpieczne rozwiązania pakietu Office](../vsto/securing-office-solutions.md)
- [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązania pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Szczególne zagadnienia dotyczące zabezpieczeń dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md)