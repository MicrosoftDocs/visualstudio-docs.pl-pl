---
title: Zabezpieczenia rozwiązań programu SharePoint | Microsoft Docs
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
ms.openlocfilehash: 16fb3e4a0e1aed14e4a3f1b3178dc753f5dc10b4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984188"
---
# <a name="security-for-sharepoint-solutions"></a>Zabezpieczenia rozwiązań programu SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obejmuje następujące funkcje, aby zwiększyć bezpieczeństwo aplikacji programu SharePoint.

## <a name="safe-control-entries"></a>Bezpieczne wpisy kontroli
 Każdy element projektu programu SharePoint utworzony w [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma właściwość **wpisów bezpiecznego sterowania** , która reprezentuje kolekcję bezpiecznych kontrolek. **Bezpieczna** podwłaściwość umożliwia określenie formantów, które są uważane za bezpieczne. Aby uzyskać więcej informacji, zobacz [udostępnianie informacji o pakiecie i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) i [Określanie bezpiecznego składniki Web Part](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#sharepoint_northwindwebparts_topic19).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers — atrybut
 Domyślnie tylko aplikacje, które są w pełni zaufane przez system w środowisku uruchomieniowym zabezpieczenia dostępu kodu (CAS), mogą uzyskać dostęp do udostępnionego zestawu kodu zarządzanego. Oznaczenie w pełni zaufanego zestawu przy użyciu atrybutu AllowPartiallyTrustedCallers umożliwia częściowo zaufanym zestawom dostęp do niego.

 Atrybut AllowPartiallyTrustedCallers jest dodawany do dowolnego rozwiązania programu SharePoint, które nie zostało wdrożone w globalnej pamięci podręcznej zestawów systemu ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Obejmuje to rozwiązania w trybie piaskownicy lub rozwiązania wdrożone w katalogu bin aplikacji programu SharePoint. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń w wersji 1 Microsoft .NET Framework](/previous-versions/msp-n-p/ff921345(v=pandp.10)) i [wdrażanie składniki Web Part w programie SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Bezpieczna przed właściwością skryptu
 *Wstrzyknięcie skryptu* polega na wstawieniu potencjalnie złośliwego kodu do formantów lub stron sieci Web. Aby ułatwić ochronę witryn programu SharePoint 2010 przed iniekcją skryptów, współautorzy nie mogą wyświetlać ani edytować części sieci Web ani ich właściwości domyślnie. Takie zachowanie jest kontrolowane przez atrybut SafeControl o nazwie SafeAgainstScript. W [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ustaw ten atrybut **w bezpiecznym** **wpisie** dla elementu projektu. Aby uzyskać więcej informacji, zobacz [udostępnianie informacji o pakiecie i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) i [instrukcje: Oznaczanie kontrolek jako bezpiecznych](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Kontrola konta użytkownika w systemach Vista i Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] i [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] obejmują funkcję zabezpieczeń znaną jako Kontrola konta użytkownika (UAC). W celu opracowania rozwiązań programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] w systemach [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] i [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] Kontrola konta użytkownika wymaga uruchomienia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jako administrator systemu. Z menu **Start** , otwórz menu skrótów dla [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], a następnie wybierz **Uruchom jako administrator**.

 Aby skonfigurować skrót [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tak, aby był zawsze uruchamiany jako administrator, otwórz jego menu skrótów, wybierz polecenie **Właściwości**, wybierz przycisk **Zaawansowane** w oknie dialogowym **Właściwości** , a następnie zaznacz pole wyboru **Uruchom jako administrator** .

 Aby uzyskać więcej informacji, zobacz artykuł [Omówienie i Konfigurowanie kontroli konta użytkownika w systemie Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). i [Kontrola konta użytkownika systemu Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Uwagi dotyczące uprawnień programu SharePoint
 Aby tworzyć rozwiązania programu SharePoint, musisz mieć wystarczające uprawnienia do uruchamiania i debugowania rozwiązań programu SharePoint. Przed przetestowaniem rozwiązania SharePoint wykonaj następujące kroki, aby upewnić się, że masz wymagane uprawnienia:

1. Dodaj konto użytkownika jako administratora w systemie.

2. Dodaj konto użytkownika jako administratora farmy dla serwera programu SharePoint.

    1. W obszarze Administracja centralna programu SharePoint 2010 wybierz łącze **Zarządzaj grupą Administratorzy farmy** .

    2. Na stronie **Administratorzy farmy** wybierz opcję menu **Nowy**

3. Dodaj konto użytkownika do grupy WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Dodatkowe zasoby zabezpieczeń
 Więcej informacji o problemach z zabezpieczeniami znajduje się w następujących tematach.

### <a name="visual-studio-security"></a>Zabezpieczenia Visual Studio

- [Uprawnienia zabezpieczeń i użytkowników](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Zabezpieczenia w kodzie natywnym i .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Zabezpieczenia w .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Zabezpieczenia programu SharePoint

- [Administracja i zabezpieczenia programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Centrum zasobów zabezpieczeń programu SharePoint](/sharepoint/dev/)

- [Zabezpieczanie składniki Web Part w programie SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Ulepszanie zabezpieczeń aplikacji sieci Web: zagrożenia i środki zaradcze](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Zabezpieczenia ogólne

- [Cykl życia w witrynie MSDN Security Development](https://www.microsoft.com/msrc?rtc=1)

- [Tworzenie bezpiecznych aplikacji ASP.NET: uwierzytelnianie, autoryzacja i Bezpieczna komunikacja](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)