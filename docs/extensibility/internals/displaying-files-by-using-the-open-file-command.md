---
title: Wyświetlanie plików za pomocą polecenia Otwórz plik | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a351846df9391881d34f53322a852cab7ebbe3b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987924"
---
# <a name="display-files-by-using-the-open-file-command"></a>Wyświetlanie plików za pomocą polecenia Otwórz plik
W poniższych krokach opisano sposób obsługi IDE **Otwórz plik** polecenia, które jest dostępne w **pliku** menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W krokach opisano również, jak projekty powinny odpowiadać na wywołania, które pochodzą z tego polecenia.  
  
 Kiedy użytkownik kliknie **Otwórz plik** polecenie **pliku** menu i wybierze plik z **Otwórz plik** odbywa się okno dialogowe następujący proces:  
  
1.  Za pomocą uruchomionej tabeli dokumentu, IDE ustala, czy plik jest już otwarty w projekcie.  
  
    -   Jeśli plik jest otwarty, IDE resurfaces okna.  
  
    -   Jeśli plik nie jest otwarty, IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> kwerendy każdego projektu w celu określenia, który projekt można otworzyć pliku.  
  
        > [!NOTE]
        >  W danej implementacji projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, podaj wartość priorytetu, który wskazuje poziom, w którym projekt zostanie otwarty plik. Wartości priorytetu znajdują się w <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczenia.  
  
2.  Każdy projekt odpowiada za pomocą poziom priorytetu, która wskazuje ważność umieszcza się go z tego projektu, można otworzyć pliku.  
  
3.  IDE używa następujących kryteriów, aby ustalić, który projekt zostanie otwarty plik:  
  
    -   Projekt, który odpowiada o najwyższym priorytecie (`DP_Intrinsic`) otwiera plik. Jeśli więcej niż jeden projekt odpowiada za pomocą tego priorytetu, pierwszy projekt na otwiera plik.  
  
    -   Jeśli projekt nie odpowiada o najwyższym priorytecie (`DP_Intrinsic`), ale wszystkie projekty odpowiadają za pomocą tego samego, dolna priorytet aktywny projekt zostanie otwarty plik. Jeśli projekt nie jest aktywna, pierwszy projekt na otwiera plik.  
  
    -   Jeśli projekt nie oświadczeń własność pliku (`DP_Unsupported`), projekcie plików otwiera plik.  
  
         Jeśli tworzone jest wystąpienie projektu różne pliki, projekt zawsze odpowiada wartością `DP_CanAddAsExternal`. Ta wartość wskazuje, że projekt można otworzyć pliku. Ten projekt jest używany do przechowywania otwartych plików, które nie są w innym projekcie. Na liście elementów w tym projekcie, nie jest trwały; Ten projekt jest widoczna w **Eksploratora rozwiązań** tylko wtedy, gdy jest używany do otwarcia pliku.  
  
         Jeśli w projekcie plików pozostałych nie wskazuje, że plik można otworzyć, wystąpienie projektu nie utworzono. W tym przypadku IDE tworzy wystąpienie projektu różne pliki i informuje projekt można otworzyć pliku.  
  
4.  Jak najszybciej IDE ustala, który projekt zostanie otwarty plik wywoływanych przez nią <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody w tym projekcie.  
  
5.  Projekt następnie ma możliwość otwarcia pliku przy użyciu edytora specyficznych dla projektu lub edytora standardowego. Aby uzyskać więcej informacji, zobacz [jak: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md) i [jak: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)odpowiednio.  
  
## <a name="see-also"></a>Zobacz także  
 [Wyświetlanie plików za pomocą polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Instrukcje: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)