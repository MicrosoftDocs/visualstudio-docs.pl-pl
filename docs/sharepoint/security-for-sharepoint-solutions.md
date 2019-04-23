---
title: Zabezpieczenia dla rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31bcd41dc1a6fd7f314c7d701f52c3728dd2ee8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040457"
---
# <a name="security-for-sharepoint-solutions"></a>Zabezpieczenia dla rozwiązań SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obejmuje następujące funkcje, aby pomóc zwiększyć bezpieczeństwo aplikacji programu SharePoint.

## <a name="safe-control-entries"></a>Wpisy bezpiecznych kontrolek
 Każdy element projektu programu SharePoint, utworzone w [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma **wpisy bezpiecznych kontrolek** właściwość, która reprezentuje bezpiecznego kontroluje kolekcji. Jego **bezpieczne** wykorzystanie pozwala na określenie formantów, które należy rozważyć bezpieczne. Aby uzyskać więcej informacji, zobacz [zawierają wdrażanie pakietów i informacje w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) i [Określanie bezpiecznych składników Web Part](http://go.microsoft.com/fwlink/?LinkId=177521).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers attribute
 Domyślnie tylko aplikacje, które są w pełni zaufana przez system zabezpieczenia dostępu kodu plików środowiska uruchomieniowego dostęp można uzyskać zestawu udostępnionego kodu zarządzanego. Oznaczanie zestawie całkowicie zaufanym o atrybucie AllowPartiallyTrustedCallers umożliwia częściowo zaufanych zestawów do niego dostęp.

 Wszystkie rozwiązania programu SharePoint, który nie jest wdrożony w globalnej pamięci podręcznej systemu jest dodawany atrybut AllowPartiallyTrustedCallers ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Obejmuje to rozwiązania w trybie piaskownicy lub rozwiązań wdrożonych do katalogu Bin aplikacji programu SharePoint. Aby uzyskać więcej informacji, zobacz [wersji 1 zmiany dotyczące zabezpieczeń platformy Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) i [wdrażania składników Web Part w SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

## <a name="safe-against-script-property"></a>Bezpieczne względem skryptu właściwości
 *Skrypt iniekcji* to wstawianie potencjalnie złośliwego kodu do kontrolki lub strony sieci Web. Aby ułatwić ochronę witryn programu SharePoint 2010 na uruchomienie skryptu, współautorzy nie Wyświetl lub Edytuj ich właściwości lub składniki Web Part domyślnie. To zachowanie jest kontrolowana przez SafeControl — atrybut o nazwie SafeAgainstScript. W [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], ustaw ten atrybut w elemencie projektu **wpisy bezpiecznych kontrolek** podwłaściwości **bezpieczne względem skryptu**. Aby uzyskać więcej informacji, zobacz [zawierają wdrażanie pakietów i informacje w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) i [jak: Oznaczanie kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Kontrola konta użytkownika 7 Vista i Windows
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] i [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] zestawowi funkcji zabezpieczeń, znane jako Kontrola konta użytkownika (UAC). Tworzenie rozwiązań programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] i [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] systemów kontroli konta użytkownika, użytkownik musi uruchomić [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] administrator systemu. Z **Start** menu, otwórz menu skrótów dla [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], a następnie wybierz **Uruchom jako administrator**.

 Aby skonfigurować [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] skrótów, aby zawsze Uruchom jako administrator, otwórz jego menu skrótów, wybierz **właściwości**, wybierz **zaawansowane** znajdujący się w **właściwości**okno dialogowe, a następnie wybierz pozycję **Uruchom jako administrator** pole wyboru.

 Aby uzyskać więcej informacji, zobacz [opis i konfigurowanie Kontrola konta użytkownika w Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). i [Kontrola konta użytkownika Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Uwagi dotyczące uprawnień programu SharePoint
 Tworzenie rozwiązań programu SharePoint, musi mieć wystarczające uprawnienia do uruchamiania i debugowania rozwiązań programu SharePoint. Przed przetestowaniem rozwiązania programu SharePoint, wykonaj następujące kroki, aby upewnić się, że masz odpowiednie uprawnienia:

1. Dodaj konto użytkownika z uprawnieniami administracyjnymi w systemie.

2. Dodaj konto użytkownika jako administratora farmy programu SharePoint server.

    1. W administracji centralnej programu SharePoint 2010, wybrać **Zarządzaj grupą administratorów farmy** łącza.

    2. Na **administratorzy farmy** wybierz **New** opcji menu

3. Dodaj konto użytkownika do grupie WSS_ADMIN_WPG uprawnienia.

## <a name="additional-security-resources"></a>Zasoby dodatkowe zabezpieczenia
 Aby uzyskać więcej informacji na temat problemów z zabezpieczeniami zobacz następujące tematy.

### <a name="visual-studio-security"></a>Zabezpieczenia Visual Studio

- [Zabezpieczenia i uprawnienia użytkownika](http://go.microsoft.com/fwlink/?LinkId=177503)

- [Zabezpieczenia w kodzie natywnym i kodzie .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)

- [Zabezpieczenia w programie .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>Zabezpieczenia programu SharePoint

- [Administracja programu SharePoint Foundation i zabezpieczenia](http://go.microsoft.com/fwlink/?LinkId=177501)

- [Centrum zasobów zabezpieczeń programu SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)

- [Zabezpieczanie składników Web Part w SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)

- [Zwiększenie zabezpieczenia aplikacji sieci Web: Zagrożenia i przeciwdziałanie](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>Zabezpieczenia ogólne

- [Cykl projektowania zabezpieczeń sieci MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)

- [Tworzenie aplikacji ASP.NET bezpiecznego: Uwierzytelniania, autoryzacji i bezpiecznej komunikacji](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)