---
title: Strona właściwości aplikacji dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 01/23/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2808afab24fa4a78d881dd23cc2b1a8efa364b2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898285"
---
# <a name="application-property-page-uwp-projects"></a>Strona właściwości aplikacji (projekty platformy uniwersalnej systemu Windows)

Użyj **aplikacji** stronę właściwości, aby określić zestaw projektu uniwersalnej platformy Windows (UWP) i informacje o pakiecie i wersji docelowej systemu Windows 10.

![Strona właściwości aplikacji](media/application-page-uwp.png)

Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu w **Eksploratora rozwiązań**. Następnie wybierz **projektu** > **właściwości** na pasku menu. Strony właściwości, Otwórz na **aplikacji** kartę.

## <a name="general-section"></a>Sekcja Ogólne

**Nazwa zestawu**&mdash;Określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu.

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Domyślny obszar nazw**&mdash;określa podstawowej przestrzeni nazw dla plików dodawane do projektu. Aby uzyskać więcej informacji na temat przestrzenie nazw, zobacz [przestrzenie nazw (C# Podręcznik programowania)](/dotnet/csharp/programming-guide/namespaces/), [przestrzeni nazw (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces), lub [przestrzenie nazw (C++)](/cpp/cpp/namespaces-cpp).

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informacje o zestawie**&mdash;wybierając ten przycisk otwiera [informacje o zestawie dialogowe](../../ide/reference/assembly-information-dialog-box.md).

**Manifest pakietu**&mdash;wybranie tego przycisku zostanie otwarty projektant manifestu. Projektant manifestu, możesz je również otworzyć, wybierając _Package.appxmanifest_ w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [skonfigurować pakiet za pomocą projektanta manifestu](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Sekcja określania wartości docelowej

Należy określić wersję docelową i minimalną wersję systemu Windows 10 dla aplikacji, przy użyciu list rozwijanych w tej sekcji. Zalecane jest, docelowych najnowszej wersji systemu Windows 10 i jeśli tworzysz aplikację przedsiębiorstwa, zbyt obsługi starszej wersji minimalnej. Aby uzyskać więcej informacji na temat wersji systemu Windows 10 do wyboru, zobacz [wybierz wersję platformy uniwersalnej systemu Windows](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Aby uzyskać informacje o platformie przeznaczonych dla programu Visual Studio 2017, zobacz [platformy](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Zobacz także

- [Tworzenie pierwszej aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/get-started/your-first-app)
- [Wybierz wersję platformy uniwersalnej systemu Windows](/windows/uwp/updates-and-versions/choose-a-uwp-version)