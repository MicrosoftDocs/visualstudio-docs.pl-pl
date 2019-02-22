---
title: 'Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc400b4e9b504b512fc8ed3ec6c6dec3e676310e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630668"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce
Możesz wdrożyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, która używa domyślnych uprawnień dla stref Internet lub lokalny Intranet. Alternatywnie można utworzyć strefę niestandardową dla określonych uprawnień wymaganych przez aplikację. Można to zrobić poprzez dostosowanie uprawnień zabezpieczeń w **zabezpieczeń** strony **projektanta projektu**.

### <a name="to-customize-a-permission"></a>Aby dostosować uprawnienia

1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2.  Kliknij przycisk **zabezpieczeń** kartę.

3.  Wybierz **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru.

4.  Wybierz **to częściowo zaufanych aplikacji** przycisku opcji.

     Formanty w **uprawnienia zabezpieczeń aplikacji ClickOnce** sekcji są włączone.

5.  Z **strefy, aplikacja zostanie zainstalowana z** listy rozwijanej kliknij **(niestandardowy)**.

6.  Kliknij przycisk **Edytuj uprawnienia XML**.

     *App.manifest* plik zostanie otwarty w edytorze XML.

7.  Przed `</applicationRequestMinimum>` elementu Dodawanie kodu XML uprawnienia, których wymaga aplikacja.

    > [!NOTE]
    >  Możesz użyć `ToXml` ustawiona metoda uprawnienia, można wygenerować kodu XML manifestu aplikacji. Na przykład, aby wygenerować plik XML dla <xref:System.Security.Permissions.EnvironmentPermission> zestaw uprawnień, wywołanie <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metody.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
