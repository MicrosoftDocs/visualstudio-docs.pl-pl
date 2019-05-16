---
title: Podstawowe informacje o typach projektów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704074"
---
# <a name="project-type-essentials"></a>Podstawowe informacje o typach projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawiera kilka typów projektów w językach takich jak [!INCLUDE[csprcs](../../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umożliwia również tworzenie własnych typów projektów.  
  
 Jeśli chcesz tylko dodać niestandardowe polecenia, edytory lub okna [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], możesz to zrobić bez tworzenia nowego typu projektu. Więcej informacji znajduje się w następujących tematach:  
  
- [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Podobnie jeśli chcesz dostosować zachowanie podane [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] typów projektów, można zrobić za pomocą podtypy projektów. Aby uzyskać więcej informacji, zobacz [podtypy projektów](../../extensibility/internals/project-subtypes.md).  
  
  Należy utworzyć nowy typ projektu dla projektów, które są oparte na język inny niż [!INCLUDE[csprcs](../../includes/csprcs-md.md)] i [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Jeśli chcesz obsługiwać co najmniej jeden z następujących czynności:  
  
- Kompilacja  
  
- wdrażania  
  
- Wiele konfiguracji  
  
- Kontrola źródła  
  
- Debugowanie  
  
- Elementy projektu w Eksploratorze rozwiązań  
  
- **Otwórz projekt** lub **nowy projekt** okien dialogowych  
  
- Zagnieżdżanie projektów  
  
- Aby uzyskać więcej informacji na temat funkcji typów projektów zobacz następujące tematy:  
  
- Typy projektów są obiektami w VSPackage, które implementują zbiór interfejsów [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oczekuje. Jeśli używasz języka C# do tworzenia typów projektów, klasy projektu środowiska pakietu zarządzanego implementacji interfejsów wymaganych dla Ciebie i umożliwiają dziedziczą tę implementację. Aby uzyskać więcej informacji, zobacz [Implementowanie typu projektu (C#) przy użyciu środowiska pakietu zarządzanego](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Dla deweloperów C++ klas w bibliotece HierUtil działają w podobny sposób. Aby uzyskać więcej informacji, zobacz [nie w kompilacji: Implementowanie typu projektu (C++) przy użyciu klasy projektu HierUtil7](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Typy projektów może obsługiwać danych innych niż pliki kodu źródłowego typowe, które są kompilowane do zestawu .exe lub .dll. Na przykład [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektów baz danych zawierają odwołania do skryptu i zapytania plików przechowywanych na dysku i dodanie poleceń do **Eksploratora rozwiązań** do wykonywania skryptów i zapytania względem bazy danych, ale projektów nie obsługują zachowanie kompilacji. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Typ projektu nie ma do korzystania z plików w ogóle. Na przykład typ projektu można przechowywać swoje dane w bazie danych. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] udostępnia typy projektów pełną kontrolę nad jak utrzymują danych dla projektów i elementów projektu. Aby uzyskać więcej informacji, zobacz [decyzje projektowe dotyczące typów projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
- Typy projektów należy podać *fabryka projektu*, który jest obiektem, który tworzy wystąpienie projektu zawsze, gdy typ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest poinformował próbę otwarcia lub utworzenia projektu, który jest oparty na tego typu projektu. Aby uzyskać więcej informacji, zobacz [tworzenia projektu wystąpień, przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Typy projektów, należy podać szablonów projektów i elementów projektu. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gdy użytkownicy tworzyć nowe projekty i dodawania nowych elementów do istniejących projektów przy użyciu szablonów. Aby uzyskać więcej informacji, zobacz [Dodawanie projektu i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Typy projektów może obsługiwać wiele konfiguracji, takich jak Debug i Release. Użytkownicy mogą zmieniać różne konfiguracje projektu za pomocą stron właściwości, które należy podać. Aby uzyskać więcej informacji, zobacz [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)
