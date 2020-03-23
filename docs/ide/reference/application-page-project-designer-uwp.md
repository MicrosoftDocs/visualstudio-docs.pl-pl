---
title: Strona właściwości aplikacji dla aplikacji platformy uniwersalnej systemu Windows
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77173090"
---
# <a name="application-property-page-uwp-projects"></a>Strona właściwości aplikacji (projekty platformy uniwersalnej systemuśpiłnie)

Strona Właściwości **aplikacji** służy do określania informacji o zestawie i pakiecie projektu platformy uniwersalnej systemu Windows (PLATFORMY UNIWERSALNEJ SYSTEMU Windows) oraz określania docelowej wersji systemu Windows 10.

![Strona właściwości aplikacji](media/application-page-uwp.png)

Aby uzyskać dostęp do strony **Aplikacji,** wybierz węzeł projektu w **Eksploratorze rozwiązań**. Następnie wybierz polecenie**Właściwości** **projektu** > na pasku menu. Strony właściwości są otwierane na karcie **Aplikacja.**

## <a name="general-section"></a>Sekcja ogólna

**Nazwa zestawu**&mdash;Określa nazwę pliku wyjściowego, który będzie zawierać manifest zestawu.

Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.AssemblyName%2A>właściwości programowo, zobacz .

**Domyślny obszar nazw**&mdash;Określa bazowy obszar nazw dla plików dodanych do projektu. Aby uzyskać więcej informacji na temat obszarów nazw, zobacz [Obszary nazw (przewodnik po programowaniu W języku C#),](/dotnet/csharp/programming-guide/namespaces/) [Obszary nazw (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces)lub [Obszary nazw (C++)](/cpp/cpp/namespaces-cpp).

Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.RootNamespace%2A>właściwości programowo, zobacz .

**Informacje o**&mdash;złożeniu Wybranie tego przycisku powoduje [wyświetlenie okna dialogowego Informacje o złożeniu](../../ide/reference/assembly-information-dialog-box.md).

**Manifest pakietu**&mdash;Wybranie tego przycisku otwiera projektanta manifestu. Projektant manifestu można również uzyskać dostęp, wybierając plik _Package.appxmanifest_ w **Eksploratorze rozwiązań**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie pakietu z projektantem manifestów](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Sekcja Kierowania

Wersję docelową i minimalną wersję systemu Windows 10 dla aplikacji można ustawić za pomocą list rozwijanych w tej sekcji. Zaleca się, aby kierować reklamy na najnowszą wersję systemu Windows 10, a jeśli tworzysz aplikację dla przedsiębiorstwa, że obsługuje starszą wersję minimalną zbyt. Aby uzyskać więcej informacji o tym, którą wersję systemu Windows 10 wybrać, zobacz [Wybieranie wersji platformy uniwersalnej](/windows/uwp/updates-and-versions/choose-a-uwp-version)systemu Windows .

Aby uzyskać informacje na temat kierowania na platformę w programie Visual Studio, zobacz [Kierowanie na platformę.](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting)

## <a name="see-also"></a>Zobacz też

- [Tworzenie pierwszej aplikacji platformy uniwersalnej systemuśpiłnie](/windows/uwp/get-started/your-first-app)
- [Wybieranie wersji platformy uniwersalnej systemu uniwersalnego](/windows/uwp/updates-and-versions/choose-a-uwp-version)
