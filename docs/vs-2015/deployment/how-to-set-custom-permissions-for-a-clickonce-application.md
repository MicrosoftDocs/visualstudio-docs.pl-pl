---
title: 'Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 279dd66ca1f814dbd52593d52040818edf8f408b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786351"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wdrożyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, która używa domyślnych uprawnień dla stref Internet lub lokalny Intranet. Alternatywnie można utworzyć strefę niestandardową dla określonych uprawnień wymaganych przez aplikację. Można to zrobić poprzez dostosowanie uprawnień zabezpieczeń w **zabezpieczeń** strony **projektanta projektu**.  
  
### <a name="to-customize-a-permission"></a>Aby dostosować uprawnienia  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **zabezpieczeń** kartę.  
  
3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.  
  
4.  Wybierz **to częściowo zaufanych aplikacji** przycisku opcji.  
  
     Formanty w **uprawnienia zabezpieczeń aplikacji ClickOnce** sekcji są włączone.  
  
5.  Z **strefy, aplikacja zostanie zainstalowana z** listy rozwijanej kliknij **(niestandardowy)**.  
  
6.  Kliknij przycisk **Edytuj uprawnienia XML**.  
  
     Plik app.manifest zostanie otwarty w edytorze XML.  
  
7.  Przed `</applicationRequestMinimum>` elementu Dodawanie kodu XML uprawnienia, których wymaga aplikacja.  
  
    > [!NOTE]
    >  Możesz użyć `ToXml` ustawiona metoda uprawnienia, można wygenerować kodu XML manifestu aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestaw uprawnień, wywołanie <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metody. Aby uzyskać więcej informacji na temat struktury uprawnienie ustawić XML, zobacz [NIB: Instrukcje: Importowanie zestawu uprawnień za pomocą pliku XML](http://msdn.microsoft.com/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
