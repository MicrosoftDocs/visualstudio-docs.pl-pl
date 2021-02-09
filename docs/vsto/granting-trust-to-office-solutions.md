---
title: Udzielanie zaufania do rozwiązań pakietu Office
description: Aby udzielić zaufania do rozwiązań pakietu Office, należy zmodyfikować zasady zabezpieczeń każdego komputera docelowego w celu zaufania do zestawu rozwiązań, manifestu wdrożenia i dokumentu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f98f3154a0708ce7a01603968f0f5774dd86f40e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910226"
---
# <a name="grant-trust-to-office-solutions"></a>Udzielanie zaufania do rozwiązań pakietu Office
  Udzielanie zaufania do rozwiązań pakietu Office oznacza modyfikację zasad zabezpieczeń każdego komputera docelowego w celu zaufania do zestawu rozwiązań, manifestu aplikacji, manifestu wdrażania i dokumentu. Zaufaniem można udzielić do rozwiązania pakietu Office przez użytkownika lub użytkowników końcowych.

 Można przyznać pełne zaufanie do rozwiązania pakietu Office, podpisywanie manifestów aplikacji i wdrażania.

 Użytkownicy końcowi mogą udzielić zaufania do rozwiązania pakietu Office, wykonując decyzję zaufania w [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monicie zaufania.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Ufaj rozwiązaniu, podpisywanie manifestów aplikacji i wdrażania
 Wszystkie manifesty aplikacji i wdrażania dla rozwiązań pakietu Office muszą być podpisane przy użyciu certyfikatu, który identyfikuje wydawcę. Certyfikaty stanowią podstawę podejmowania decyzji dotyczących zaufania.

 Certyfikat tymczasowy jest tworzony dla Ciebie i ma przyznane zaufanie w czasie kompilacji, dzięki czemu rozwiązanie zostanie uruchomione podczas debugowania. Jeśli opublikujesz rozwiązanie podpisane przy użyciu certyfikatu tymczasowego, użytkownik końcowy będzie monitowany o podjęcie decyzji o zaufaniu.

 Po podpisaniu rozwiązania przy użyciu znanego i zaufanego certyfikatu rozwiązanie zostanie automatycznie zainstalowane bez monitowania użytkownika końcowego o podjęcie decyzji o zaufaniu. Aby uzyskać więcej informacji na temat uzyskiwania certyfikatu do podpisywania, zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md). Po uzyskaniu certyfikatu certyfikat musi być jawnie zaufany przez dodanie go do listy zaufanych wydawców. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Jeśli deweloper zarejestruje rozwiązanie z certyfikatem tymczasowym, administrator może ponowne podpisać dostosowanie przy użyciu znanego i zaufanego certyfikatu za pomocą Narzędzie tworzenia i edycji manifestów (*mage.exe*), który jest jednym z narzędzi Microsoft .NET Framework. Aby uzyskać więcej informacji o rozwiązaniach podpisywania, zobacz jak: podpisywanie [rozwiązań pakietu Office](../vsto/how-to-sign-office-solutions.md) i [instrukcje: podpisywanie aplikacji i manifestów wdrożenia](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Ufaj rozwiązaniu przy użyciu monitu zaufania ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] poprosi użytkownika końcowego o podjęcie decyzji o zaufaniu, jeśli nie ma żadnych zasad, które ufają certyfikatowi rozwiązania. Jeśli użytkownik końcowy przyznaje zaufanie do rozwiązania, zostanie utworzony wpis listy dołączania zawierający adres URL i klucz publiczny do przechowywania tej decyzji zaufania. Gdy zaufane dostosowanie zostanie uruchomione później, użytkownik końcowy nie będzie ponownie monitowany.

 Administratorzy mogą wyłączyć [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monit zaufania lub wymagać, aby monit zarejestrował się tylko w przypadku rozwiązań podpisanych za pomocą certyfikatu Authenticode. Aby uzyskać więcej informacji na temat zmiany tych ustawień dla stref mójkomputer, LocalIntranet, Internet, TrustedSites i UntrustedSites, zobacz How to [: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)
- [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)
- [Szczególne zagadnienia dotyczące zabezpieczeń rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md)