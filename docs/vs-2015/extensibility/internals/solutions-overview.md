---
title: Omówienie rozwiązań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d9eb36da433575710ae7f24da85e4a1a0970b79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781065"
---
# <a name="solutions-overview"></a>Omówienie rozwiązań
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozwiązanie to grupa jeden lub więcej projektów, które współpracują ze sobą, aby utworzyć aplikację. Informacje o projekcie i stanie odnoszących się do rozwiązania są przechowywane w dwóch plikach innego rozwiązania. Plik rozwiązania (.sln) są oparte na tekście umieszczone pod kontrolą kodu źródłowego i udostępniana między użytkownikami i. Plik opcji (suo) użytkownika rozwiązania jest plikiem binarnym. Co w efekcie plik .suo nie można umieścić pod kontrolą kodu źródłowego i zawiera informacje specyficzne dla użytkownika.  
  
 Dowolnego pakietu VSPackage można zapisać do dowolnego typu pliku rozwiązania. Ze względu na charakter pliki istnieją dwa różne interfejsy implementowane był na nich zapis. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Interfejsu zapisuje informacje tekstowe do pliku .sln i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfejsu zapisuje plik .suo strumieni binarnych.  
  
> [!NOTE]
>  Projekt nie ma jawnie zapisu wykorzystywany do pliku rozwiązania. środowisko sobie z nimi poradzi dla projektu. W związku z tym chyba że chcesz dodać dodatkową zawartość do pliku rozwiązania, nie trzeba zarejestrować Twojego pakietu VSPackage w ten sposób.  
  
 Każdego pakietu VSPackage obsługi trwałości rozwiązanie używa trzech interfejsów <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejs, który jest implementowany przez środowisko i wywoływany przez pakietu VSPackage, i `IVsPersistSolutionProps` i `IVsPersistSolutionOpts`, które są zarówno implementowane przez pakietu VSPackage. `IVsPersistSolutionOpts` Interfejsu tylko musi zostać wdrożone, jeśli ma on zostać zapisany przez pakietu VSPackage plik .suo informacje prywatne.  
  
 Po otwarciu rozwiązania odbywa się następujący proces.  
  
1. Środowisko odczytuje rozwiązania.  
  
2. Jeśli znajdzie środowiska `CLSID`, ładuje odpowiedniego pakietu VSPackage.  
  
3. Jeśli pakietu VSPackage jest ładowany, wywołania środowiska `QueryInterface` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfejsu dla interfejsu, który wymaga pakietu VSPackage.  
  
   1.  Podczas odczytu z pliku SLN, środowisko wywołuje `QueryInterface` dla `IVsPersistSolutionProps`.  
  
   2.  Podczas odczytywania z pliku .suo, środowisko wywołuje `QueryInterface` dla `IVsPersistSolutionOpts`.  
  
   Szczegółowe informacje dotyczące korzystania z tych plików można znaleźć w [rozwiązania (. Plik sln)](../../extensibility/internals/solution-dot-sln-file.md) i [opcje użytkownika rozwiązania (. Plik suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Jeśli chcesz utworzyć nową konfigurację rozwiązania składający się z dwóch projektów konfiguracje z wyłączeniem trzecią z kompilacji, należy użyć interfejsu użytkownika strony właściwości lub automatyzacji. Nie można zmienić konfiguracji Menedżera kompilacji rozwiązania i ich właściwości bezpośrednio, ale można manipulować Menedżera kompilacji rozwiązania przy użyciu `SolutionBuild` klasy z obiektu DTE w modelu automatyzacji. Aby uzyskać więcej informacji na temat konfigurowania rozwiązania, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

