---
title: Strona właściwości aplikacji dla aplikacji platformy UWP
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3c8f72d4e1d1caeacd5dfefef5310dc2cef83b92
ms.sourcegitcommit: 83d9f2b56955f7a5267a1438bb28ef804775f88b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2020
ms.locfileid: "77173090"
---
# <a name="application-property-page-uwp-projects"></a>Strona właściwości aplikacji (projekty platformy UWP)

Na stronie właściwości **aplikacji** można określić zestaw i informacje o projekcie platforma uniwersalna systemu Windows (platformy UWP) oraz docelową wersję systemu Windows 10.

![Strona właściwości aplikacji](media/application-page-uwp.png)

Aby uzyskać dostęp do strony **aplikacji** , wybierz węzeł projektu w **Eksplorator rozwiązań**. Następnie wybierz pozycję **Project** > **Właściwości** na pasku menu. Strony właściwości są otwierane na karcie **aplikacja** .

## <a name="general-section"></a>Sekcja ogólna

**Nazwa zestawu**&mdash;określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu.

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Domyślna przestrzeń nazw**&mdash;określa podstawową przestrzeń nazw dla plików dodanych do projektu. Aby uzyskać więcej informacji na temat przestrzeni nazw, zobacz [przestrzenie nazw (C# Przewodnik programowania)](/dotnet/csharp/programming-guide/namespaces/), [przestrzenie nazw (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)lub [przestrzenie nazw (C++)](/cpp/cpp/namespaces-cpp).

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informacje o zestawie**&mdash;wybranie tego przycisku powoduje wyświetlenie okna [dialogowego Informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md).

**Manifest pakietu**&mdash;wybranie tego przycisku powoduje otwarcie projektanta manifestu. Można również uzyskać dostęp do projektanta manifestu, wybierając plik _Package. appxmanifest_ w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [Configure a Package with manifest Designer](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Sekcja określania wartości docelowej

Możesz ustawić wersję docelową i minimalną wersję systemu Windows 10 dla swojej aplikacji, używając list rozwijanych w tej sekcji. Zaleca się, aby można było określić najnowszą wersję systemu Windows 10 i jeśli tworzysz aplikację dla przedsiębiorstw, która obsługuje starszą wersję minimalną. Aby uzyskać więcej informacji na temat wersji systemu Windows 10, zobacz [Wybieranie wersji platformy UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Aby uzyskać informacje dotyczące platformy docelowej w programie Visual Studio, zobacz temat [Określanie platformy docelowej](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Zobacz także

- [Tworzenie pierwszej aplikacji platformy UWP](/windows/uwp/get-started/your-first-app)
- [Wybierz wersję platformy UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
