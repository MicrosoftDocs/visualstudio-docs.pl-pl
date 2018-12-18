---
title: Tworzenie wystąpień projektów przy użyciu fabryk projektów | Dokumentacja firmy Microsoft
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
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358c13bdc8bc312a479b9c316fa516ad68b10630
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736259"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Tworzenie wystąpień projektów przy użyciu fabryk projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typów projektów w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] użyj *fabryka projektu* do tworzenia wystąpień obiektów projektu. Fabryka projektu jest podobna do fabryki klas standard dla obiektów COM, cocreatable. Obiekty projektu nie są jednak cocreatable: one można tworzyć tylko za pomocą fabryki projektu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE wywołuje fabryka projektu zaimplementowane w swojej pakietu VSPackage, gdy użytkownik wczytuje istniejący projekt lub tworzy nowy projekt w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Nowy obiekt project zawiera środowisko IDE z wystarczającą ilość informacji, aby wypełnić Eksploratora rozwiązań. Nowy obiekt projektu także interfejsami wymaganymi do obsługi wszystkich odpowiednich akcji UI inicjowane przez środowisko IDE.  
  
 Możesz zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejsu w klasie w projekcie. Zazwyczaj znajduje się w module swój własny.  
  
 Na przykład implementacja `IVsProjectFactory` interfejsu, zobacz PrjFac.cpp, który jest zawarty w [podstawowego projektu](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) katalog przykładu.  
  
 Projekty, które obsługuje Agregacja przez właściciela, muszą zostać zachowane klawiszem właściciela w pliku projektu. Gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metoda jest wywoływana w projekcie przy użyciu klucza właściciela, należących do projektu konwertuje jego właściciela klucza fabryką projektu, następnie wywołuje GUID `CreateProject` metody w tej fabryce projektu w celu utworzenia rzeczywistych.  
  
## <a name="creating-an-owned-project"></a>Tworzenie projektu należące do firmy  
 Właściciel tworzy projekt należące do firmy w dwóch fazach:  
  
1. Przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. Zapewnia możliwość tworzenia obiektu projektu zagregowane oparte na danych wejściowych kontrolowanie należących do projektu `IUnknown`. Należących do projektu przekazuje wewnętrzny `IUnknown` i zagregowane obiekt do projektu właściciela. Daje możliwość przechowywania wewnętrzny należących do projektu `IUnknown`.  
  
2. Przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Należących do projektu nie wszystkie jego wystąpienia, gdy ta metoda jest wywoływana zamiast wywoływać metodę `IVsProjectFactory::CreateProject` tak jak w przypadku projektów, które nie należą do. Dane wejściowe `VSOWNEDPROJECTOBJECT` wyliczenie jest zazwyczaj zagregowane należących do projektu. Należących do projektu, można użyć tej zmiennej do określenia, czy jego obiektu projektu już istnieje (plik cookie nie jest równa NULL) lub musi zostać utworzona (plik cookie jest równa NULL).  
  
   Typy projektów są identyfikowane przez projekt Unikatowy identyfikator GUID, podobnie jak identyfikator CLSID cocreatable obiektu COM. Zazwyczaj jeden projekt fabryka obsługuje tworzenia wystąpień typu pojedynczego projektu, mimo że można mieć jedną fabryka projektu obsługiwać więcej niż jeden identyfikator GUID typu projektu.  
  
   Typy projektów są skojarzone z rozszerzeniem nazwy pliku określonej. Po użytkownik próbuje otworzyć istniejący plik projektu lub podejmuje próbę utworzenia nowego projektu przez Sklonowanie szablonu, IDE używa rozszerzenia w pliku w celu określenia odpowiedniego identyfikatora GUID projektu.  
  
   Jak najszybciej IDE ustala, czy należy utworzyć nowy projekt lub Otwórz istniejący projekt określonego typu, IDE używa informacji w rejestrze systemowym w obszarze [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] do ustalone, które Pakietu VSPackage implementuje fabryki wymagane projekty. IDE ładuje tego pakietu VSPackage. W <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metody pakietu VSPackage należy zarejestrować jego fabryka projektu środowiska IDE, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metody.  
  
   Podstawową metodą `IVsProjectFactory` interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> której powinna obsługiwać dwa scenariusze: otwierania istniejącego projektu i tworzenia nowego projektu. Większość projektów przechowywania ich stanu projektu w pliku projektu. Zazwyczaj nowe projekty są tworzone przez tworzenie kopii pliku szablonu jest przekazywany do `CreateProject` metody, a następnie otwarcie kopii. Istniejące projekty są tworzone przez bezpośrednio, otwierając plik projektu przekazany do `CreateProject` metody. `CreateProject` Metoda można wyświetlić dodatkowe funkcje interfejsu użytkownika dla użytkownika, zgodnie z potrzebami.  
  
   Projekt można również użyć żadne pliki, a zamiast tego należy przechowywać stanu projektu w mechanizm magazynu innego niż system plików, takich jak bazy danych lub serwer sieci Web. W tym przypadku parametr nazwy pliku jest przekazywane do `CreateProject` metoda nie jest faktycznie ścieżka systemu plików, ale unikatowy ciąg — adres URL — do identyfikowania danych projektu. Nie należy skopiować pliki szablonów, które są przekazywane do `CreateProject` do wyzwolenia sekwencji konstrukcji odpowiednie do wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)

