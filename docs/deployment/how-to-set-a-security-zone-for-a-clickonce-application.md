---
title: 'Instrukcje: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0da7c3d4129102339eaf74fac815f086e027a4f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980677"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Instrukcje: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce
Podczas ustawiania dostępu kodu uprawnień zabezpieczeń dla aplikacji ClickOnce, należy uruchomić podstawowy zestaw uprawnień na **zabezpieczeń** strony **projektanta projektu**.  
  
 W większości przypadków można także **Internet** strefy, który zawiera ograniczony zestaw uprawnień lub **lokalny Intranet** strefy, który zawiera większy zestaw uprawnień. Jeśli aplikacja wymaga uprawnień niestandardowych, możesz to zrobić, wybierając **niestandardowe** strefy zabezpieczeń. Aby uzyskać więcej informacji na temat ustawiania uprawnień niestandardowych, zobacz [jak: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Aby ustawienie strefy zabezpieczeń  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
4.  Wybierz **to częściowo zaufanych aplikacji** przycisku opcji.  
  
     Formanty w **uprawnienia zabezpieczeń aplikacji ClickOnce** sekcji są włączone.  
  
5.  W **strefy, aplikacja zostanie zainstalowana z** listy rozwijanej wybierz strefę zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
