---
title: Pola okna właściwości i interfejsy | Microsoft Docs
description: Dowiedz się więcej o wyborze, który określa, jakie informacje są wyświetlane w okno Właściwości na podstawie okna, które ma fokus w Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a74e82480d1a4c71179c0e0b0671bac4ae97191
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899631"
---
# <a name="properties-window-fields-and-interfaces"></a>Pola i interfejsy okna właściwości
Model wyboru w celu określenia, jakie informacje są wyświetlane w **oknie** Właściwości, jest oparty na oknie, które ma fokus w idee. Każde okno i obiekt w wybranym oknie mogą mieć obiekt kontekstu wyboru wypchniętą do kontekstu wyboru globalnego. Środowisko aktualizuje kontekst wyboru globalnego przy użyciu wartości z ramki okna, gdy to okno ma fokus. Po zmianie fokusu kontekst wyboru jest zmieniany.

## <a name="tracking-selection-in-the-ide"></a>Śledzenie wyboru w idee
 Ramka okna lub lokacja, należąca do środowiska IDE, ma usługę o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Poniższe kroki pokazują, w jaki sposób zaimplementowana jest zmiana zaznaczenia spowodowana przez zmianę fokusu przez użytkownika na **inne otwarte** okno lub wybranie innego elementu projektu w programie Eksplorator rozwiązań w celu zmiany zawartości wyświetlanej w oknie **Właściwości.**

1. Obiekt utworzony przez pakiet VSPackage, który znajduje się w wybranym oknie, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> wywołuje element , aby wywołać element <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Kontener wyboru dostarczony przez wybrane okno tworzy własny <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> obiekt. Po zmianie wyboru pakiet VSPackage wywołuje w celu powiadomienia wszystkich odbiorników w środowisku, w tym okna <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Właściwości, o  zmianie. Zapewnia również dostęp do informacji o hierarchii i elementach związanych z nowym wyborem.

3. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie wybranych elementów hierarchii w `VSHPROPID_BrowseObject` parametrze wypełnia obiekt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

4. Obiekt pochodzący z [interfejsu IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) jest zwracany dla [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) żądanego elementu, a środowisko opakuje go w element <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (zobacz poniższy krok). Jeśli wywołanie nie powiedzie się, środowisko wykonuje drugie wywołanie do , przekazując do niego kontener `IVsHierarchy::GetProperty` [wyboru __VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) który dostarcza element lub elementy hierarchii.

    Pakiet VSPackage projektu nie jest tworzyć, ponieważ w jego imieniu jest konstruowana konstrukcja okna vsPackage dostarczonego przez środowisko, które go <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> implementuje (na przykład **Eksplorator rozwiązań** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ).

5. Środowisko wywołuje metody metody w celu uzyskania obiektów na podstawie interfejsu w <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> celu wypełnienia okna `IDispatch` Właściwości. 

   Gdy wartość w oknie **Właściwości** zostanie zmieniona, pakiet VSPackages implementuje elementy i w celu zgłoszenia zmiany `IVsTrackSelectionEx::OnElementValueChangeEx` wartości `IVsTrackSelectionEx::OnSelectionChangeEx` elementu. Następnie środowisko wywołuje metody lub w celu zachowania informacji wyświetlanych w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> **oknie Właściwości** zsynchronizowanych z wartościami właściwości. Aby uzyskać więcej informacji, zobacz [Aktualizowanie wartości właściwości w oknie Właściwości](#updating-property-values-in-the-properties-window).

   Oprócz wybrania innego elementu projektu w programie **Eksplorator rozwiązań** w celu wyświetlenia właściwości powiązanych z tym elementem można również wybrać inny obiekt z poziomu okna formularza lub dokumentu przy użyciu listy rozwijanej dostępnej w oknie **Właściwości.** Aby uzyskać więcej informacji, zobacz [Lista obiektów okna właściwości](../../extensibility/internals/properties-window-object-list.md).

   Możesz zmienić sposób wyświetlania informacji  w siatce okna Właściwości z alfabetycznych na podzielone na grupy, a jeśli są dostępne, możesz również otworzyć stronę właściwości dla wybranego obiektu, klikając odpowiednie przyciski w oknie **Właściwości.** Aby uzyskać więcej informacji, zobacz [Przyciski okna właściwości](../../extensibility/internals/properties-window-buttons.md) i Strony [właściwości](../../extensibility/internals/property-pages.md).

   Na koniec dolna część **okna Właściwości** zawiera również opis pola wybranego w **siatce okna** Właściwości. Aby uzyskać więcej informacji, zobacz [Pobieranie opisów pól z okna właściwości](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Aktualizowanie wartości właściwości w oknie właściwości
Istnieją dwa sposoby synchronizowania okna **Właściwości** ze zmianami wartości właściwości. Pierwszym z nich jest wywołanie interfejsu , który zapewnia dostęp do podstawowych funkcji obsługi okien, w tym dostępu do narzędzi i okien dokumentów dostarczanych przez środowisko oraz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> tworzenia tych okien. W poniższych krokach opisano ten proces synchronizacji.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości przy użyciu programu IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości przy użyciu interfejsu IVsUIShell

1. Wywołaj (za pośrednictwem usługi) za każdym razem, gdy pakiet VSPackages, projekty lub edytory muszą tworzyć lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> wyliczać okna narzędzi lub dokumentów.

2. Zaimekuj , aby zachować synchronizację okna Właściwości ze zmianami właściwości dla projektu (lub dowolnego innego wybranego obiektu przeglądanego przez okno Właściwości) bez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> implementowania i   <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> wyzwalania <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> zdarzeń.

3. Zaim implementuj metody oraz , aby odpowiednio ustanawiać i wyłączać powiadomienia klienta o zdarzeniach hierarchii bez konieczności implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> hierarchii programu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .

### <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości przy użyciu IConnection
 Drugim sposobem zachowania  synchronizacji okna Właściwości ze zmianami wartości właściwości jest zaimplementowanie na obiekcie, który można połączyć, aby wskazać istnienie `IConnection` interfejsów wychodzących. Jeśli chcesz zlokalizowanej nazwy właściwości, należy uzyskać obiekt z <xref:System.ComponentModel.ICustomTypeDescriptor> . Implementacja <xref:System.ComponentModel.ICustomTypeDescriptor> może modyfikować zwracane deskryptory właściwości i zmieniać nazwę właściwości. Aby localizować opis, utwórz atrybut, który pochodzi od właściwości Description i <xref:System.ComponentModel.DescriptionAttribute> zastąp go.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Zagadnienia dotyczące implementowania interfejsu IConnection

1. `IConnection` zapewnia dostęp do obiektu podrzędnego modułu wyliczania za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu . Zapewnia również dostęp do wszystkich obiektów podrzędnych punktu połączenia, z których każdy implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs.

2. Każdy obiekt przeglądania jest odpowiedzialny za implementację <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> zdarzenia. W **oknie** Właściwości pojawi się porada dla zdarzenia ustawionego za pomocą polecenia `IConnection` .

3. Punkt połączenia określa, ile połączeń (co najmniej jedno) umożliwia w implementacji programu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Punkt połączenia, który zezwala tylko na jeden interfejs, może <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> zwracać z <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> metody .

4. Klient może wywołać interfejs w celu uzyskania dostępu do obiektu podrzędnego modułu wyliczania `IConnection` za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfejsu . Interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> może być następnie wywoływany w celu wyliczenia punktów połączenia dla każdego identyfikatora interfejsu wychodzącego (IID).

5. `IConnection` Można również wywołać , aby uzyskać dostęp do obiektów podrzędnych punktu połączenia za <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pomocą interfejsu dla każdego wychodzącego IID. Za pośrednictwem interfejsu klient uruchamia lub kończy pętlę poradnika z obiektem, który można połączyć, i <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> synchronizacją klienta. Klient może również wywołać interfejs w celu uzyskania obiektu modułu wyliczania z interfejsem w celu wyliczenia połączeń, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> które zna.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Pobieranie opisów pól z okna właściwości
W dolnej części **okna Właściwości** w obszarze opisu są wyświetlane informacje powiązane z polem wybranej właściwości. Ta funkcja jest domyślnie włączona. Jeśli chcesz ukryć pole opisu, kliknij prawym przyciskiem myszy okno **Właściwości** i kliknij polecenie **Opis.** Spowoduje to również usunięcie znacznika wyboru obok **tytułu** Opis w oknie menu. Możesz ponownie wyświetlić pole, korzystając z tych samych kroków, aby ponownie włączyć **opis.**

 Informacje w polu opisu pochodzą z tematu <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Każda metoda, interfejs, coclass i tak dalej może mieć niezlokalizowany `helpstring` atrybut w bibliotece typów. Okno **Właściwości** pobiera ciąg z pliku <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Aby określić zlokalizowane ciągi pomocy

1. Dodaj atrybut `helpstringdll` do instrukcji library w bibliotece typów ( `typelib` ).

   > [!NOTE]
   > Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku biblioteki obiektów (olb).

2. Określ `helpstringcontext` atrybuty ciągów. Można również określić `helpstring` atrybuty.

    Te atrybuty różnią się od atrybutów i , które są `helpfile` `helpcontext` zawarte w rzeczywistych tematach pomocy pliku .chm.

   Aby pobrać informacje o opisie, które mają  być wyświetlane dla wyróżnione nazwy właściwości, okno Właściwości wywołuje dla wybranej właściwości, określając żądany atrybut dla ciągu <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> `lcid` wyjściowego. Wewnętrznie znajduje plik .dll określony w atrybutie i wywołuje na tym .dll <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> `helpstringdll` z określonym `DLLGetDocumentation` kontekstem i `lcid` atrybutem.

   Podpis i implementacja `DLLGetDocumentation` programu to:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 Funkcja `DLLGetDocumentation` musi być eksportem zdefiniowanym w pliku def dla biblioteki DLL.

 Wewnętrznie tworzony jest plik olb, który w rzeczywistości jest biblioteką DLL. Ta biblioteka DLL zawiera jeden zasób, plik biblioteki typów (tlb) i jedną wyeksportowaną funkcję , `DLLGetDocumentation` .

 W przypadku plików .olb atrybut jest opcjonalny, ponieważ jest to ten sam plik, który `helpstringdll` zawiera sam plik tlb.

 Aby ciągi były wyświetlane w **okienku** Opisy, w związku z tym minimalnym wymogiem jest określenie atrybutu `helpstring` w bibliotece typów. Jeśli chcesz, aby te ciągi były zlokalizowane, musisz określić (opcjonalnie) atrybut i (wymagany) atrybut i `helpstringdll` `helpstringcontext` zaimplementować `DLLGetDocumentation` .

 Nie ma żadnych dodatkowych interfejsów, które należy zaimplementować podczas uzyskiwania zlokalizowanych informacji za pośrednictwem atrybutu idl `helpstringcontext` i `DLLGetDocumentation` .

 Innym sposobem uzyskania zlokalizowanej nazwy i opisu właściwości jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> zaimplementowanie . Aby uzyskać więcej informacji dotyczących implementacji tej metody, zobacz [Właściwości pól okna i interfejsów](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
