---
title: Strona właściwości aplikacji dla aplikacji platformy UWP
description: Dowiedz się, jak za pomocą strony aplikacji określić zestaw i informacje o projekcie platforma uniwersalna systemu Windows (platformy UWP) oraz wersję docelową systemu Windows 10.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 21dd08f81802661cae9d77ee3449f4e9369ca768
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965086"
---
# <a name="application-property-page-uwp-projects"></a>Strona właściwości aplikacji (projekty platformy UWP)

Na stronie właściwości **aplikacji** można określić zestaw i informacje o projekcie platforma uniwersalna systemu Windows (platformy UWP) oraz docelową wersję systemu Windows 10.

![Strona właściwości aplikacji](media/application-page-uwp.png)

Aby uzyskać dostęp do strony **aplikacji** , wybierz węzeł projektu w **Eksplorator rozwiązań**. Następnie wybierz   >  **Właściwości** projektu na pasku menu. Strony właściwości są otwierane na karcie **aplikacja** .

## <a name="general-section"></a>Sekcja ogólna

**Nazwa zestawu** &mdash; Określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu.

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

**Domyślna przestrzeń nazw** &mdash; Określa podstawową przestrzeń nazw dla plików dodanych do projektu. Aby uzyskać więcej informacji na temat przestrzeni nazw, zobacz [przestrzenie nazw (Przewodnik programowania w języku C#)](/dotnet/csharp/programming-guide/namespaces/), [przestrzenie nazw (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)lub [przestrzenie nazw (C++)](/cpp/cpp/namespaces-cpp).

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

**Informacje o zestawie** &mdash; Wybranie tego przycisku powoduje wyświetlenie okna [dialogowego Informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md).

**Manifest pakietu** &mdash; Wybranie tego przycisku powoduje otwarcie projektanta manifestu. Można również uzyskać dostęp do projektanta manifestu, wybierając plik _Package. appxmanifest_ w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [Configure a Package with manifest Designer](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Sekcja określania wartości docelowej

Możesz ustawić wersję docelową i minimalną wersję systemu Windows 10 dla swojej aplikacji, używając list rozwijanych w tej sekcji. Zaleca się, aby można było określić najnowszą wersję systemu Windows 10 i jeśli tworzysz aplikację dla przedsiębiorstw, która obsługuje starszą wersję minimalną. Aby uzyskać więcej informacji na temat wersji systemu Windows 10, zobacz [Wybieranie wersji platformy UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Aby uzyskać informacje dotyczące platformy docelowej w programie Visual Studio, zobacz temat [Określanie platformy docelowej](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Zobacz też

- [Tworzenie pierwszej aplikacji platformy UWP](/windows/uwp/get-started/your-first-app)
- [Wybierz wersję platformy UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
