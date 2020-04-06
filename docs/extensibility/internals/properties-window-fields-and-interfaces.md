---
title: Właściwości Pola okienne i interfejsy | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706165"
---
# <a name="properties-window-fields-and-interfaces"></a>Pola i interfejsy okna właściwości
Model do wyboru, aby określić, jakie informacje są wyświetlane w oknie Właściwości jest oparty na oknie, które ma **fokus** w IDE. Każde okno i obiekt w wybranym oknie mogą mieć jego obiekt kontekstu zaznaczenia wypchnięty do kontekstu zaznaczenia globalnego. Środowisko aktualizuje kontekst zaznaczenia globalnego z wartościami z ramki okna, gdy to okno ma fokus. Gdy fokus się zmieni, podobnie jak kontekst zaznaczenia.

## <a name="tracking-selection-in-the-ide"></a>Śledzenie wyboru w IDE
 Ramka okna lub lokacja, należąca do <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE, ma usługę o nazwie . Poniższe kroki pokazują, jak zmiana zaznaczenia, spowodowana przez użytkownika, zmieniając fokus na inne otwarte okno lub wybierając inny element projektu w **Eksploratorze rozwiązań,** jest zaimplementowana w celu zmiany zawartości wyświetlanej w oknie **Właściwości.**

1. Obiekt utworzony przez vsPackage, który znajduje się <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> w <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> wybranym <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>oknie wywołuje wywołać .

2. Kontener wyboru, dostarczony przez wybrane okno, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> tworzy własny obiekt. Po zmianie zaznaczenia VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> wywołuje powiadamianie wszystkich odbiorników w środowisku, w tym **właściwości** okna, o zmianie. Zapewnia również dostęp do hierarchii i informacji o elemencie związanych z nowym wyborem.

3. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> i przekazanie go wybrane `VSHPROPID_BrowseObject` elementy hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> w parametrze wypełnia obiekt.

4. Obiekt pochodzący z [interfejsu IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) jest zwracany dla [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) żądanego elementu, a środowisko zawija go <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> do (zobacz następujący krok). Jeśli wywołanie nie powiedzie się, `IVsHierarchy::GetProperty`środowisko wykonuje drugie wywołanie , przekazując go kontenera wyboru [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) które dostarczają towary lub towary hierarchii.

    Projekt VSPackage nie <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> tworzy, ponieważ środowisko dostarczone okno VSPackage, który implementuje go <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (na przykład **Eksplorator rozwiązań)** tworzy w jego imieniu.

5. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> metody, aby uzyskać obiekty na `IDispatch` podstawie interfejsu, aby wypełnić **właściwości** okna.

   Po zmianie wartości w oknie **Właściwości,** VSPackages implementują `IVsTrackSelectionEx::OnElementValueChangeEx` i `IVsTrackSelectionEx::OnSelectionChangeEx` zgłaszają zmianę wartości elementu. Środowisko następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> lub zachować informacje wyświetlane w oknie Właściwości zsynchronizowane z **wartościami** właściwości. Aby uzyskać więcej informacji, zobacz [Aktualizowanie wartości właściwości w oknie Właściwości](#updating-property-values-in-the-properties-window).

   Oprócz wybrania innego elementu projektu w **Eksploratorze rozwiązań,** aby wyświetlić właściwości związane z tym elementem, można również wybrać inny obiekt z okna formularza lub dokumentu przy użyciu listy rozwijanej dostępnej w oknie **Właściwości.** Aby uzyskać więcej informacji, zobacz [Właściwości listy obiektów okna](../../extensibility/internals/properties-window-object-list.md).

   Można zmienić sposób wyświetlania informacji w siatce okna **Właściwości** z alfabetycznych na kategoryczne, a jeśli jest dostępna, można również otworzyć stronę właściwości dla zaznaczonego obiektu, klikając odpowiednie przyciski w oknie **Właściwości.** Aby uzyskać więcej informacji, zobacz [Właściwości przyciski okien](../../extensibility/internals/properties-window-buttons.md) i [strony właściwości](../../extensibility/internals/property-pages.md).

   Na koniec w dolnej części okna **Właściwości** zawiera również opis pola wybranego w **siatce** okna Właściwości. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie opisów pól z okna Właściwości](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Aktualizowanie wartości właściwości w oknie Właściwości
Istnieją dwa sposoby, aby zachować właściwości okna w synchronizacji ze **zmianami** wartości właściwości. Pierwszym z nich <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> jest wywołanie interfejsu, który zapewnia dostęp do podstawowych funkcji okienowania, w tym dostępu do i tworzenia okien narzędzi i dokumentów dostarczonych przez środowisko. W poniższych krokach opisano ten proces synchronizacji.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualizowanie wartości właściwości przy użyciu funkcji IVsUiShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Aby zaktualizować wartości właściwości przy użyciu interfejsu IVsUIShell

1. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> (za pośrednictwem usługi) w dowolnym momencie, że VSPackages, projekty lub edytory trzeba utworzyć lub wyliczyć narzędzia lub okna dokumentu.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> Implementacja, aby zachować właściwości okna w synchronizacji ze **zmianami** właściwości dla projektu (lub innego <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> wybranego <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> obiektu przeglądane przez **właściwości** okna) bez implementowania i wypalania zdarzeń.

3. Zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> ustanowić i wyłączyć, odpowiednio, powiadomienie klienta <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>o zdarzeniach hierarchii bez konieczności implementacji hierarchii .

### <a name="updating-property-values-using-iconnection"></a>Aktualizowanie wartości właściwości przy użyciu funkcji IConnection
 Drugim sposobem, aby zachować właściwości okna w synchronizacji `IConnection` ze **zmianami** wartości właściwości jest zaimplementowanie na connectable obiektu, aby wskazać istnienie interfejsów wychodzących. Jeśli chcesz zlokalizować nazwę właściwości, należy wyprowadzić obiekt z pliku <xref:System.ComponentModel.ICustomTypeDescriptor>. Implementacja <xref:System.ComponentModel.ICustomTypeDescriptor> może modyfikować deskryptory właściwości, które zwraca i zmienić nazwę właściwości. Aby zlokalizować opis, należy utworzyć atrybut, <xref:System.ComponentModel.DescriptionAttribute> który pochodzi z i zastąpić Description właściwości.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Uwagi dotyczące wdrażania interfejsu IConnection

1. `IConnection`zapewnia dostęp do podobioracie modułu <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> wyliczanego z interfejsem. Zapewnia również dostęp do wszystkich pod obiektów punktu połączenia, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> z których każdy implementuje interfejs.

2. Każdy obiekt przeglądania jest odpowiedzialny <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> za implementowanie zdarzenia. Okno **Właściwości** doradzi zdarzenie ustawione `IConnection`za pośrednictwem .

3. Punkt połączenia kontroluje liczbę połączeń (jeden lub więcej) umożliwia <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>w jego realizacji . Punkt połączenia, który pozwala tylko <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> jeden <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> interfejs może powrócić z metody.

4. Klient może wywołać interfejs, `IConnection` aby uzyskać dostęp do obiektu <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> podrzędnego modułu wyliczacza z interfejsem. Interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> można następnie wywołać, aby wyliczyć punkty połączenia dla każdego identyfikatora interfejsu wychodzącego (IID).

5. `IConnection`można również wywołać w celu uzyskania dostępu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> do pod obiektów punktu połączenia z interfejsem dla każdego wychodzącego identyfikatora. Za <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pośrednictwem interfejsu klient uruchamia lub kończy pętlę doradczą z obiektem do podłączenia i własną synchronizacją klienta. Klient może również <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> wywołać interfejs, aby uzyskać obiekt <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> modułu wyliczacza z interfejsem, aby wyliczyć połączenia, o których wie.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Uzyskiwanie opisów pól z okna Właściwości
W dolnej części okna **Właściwości** w obszarze opisu są wyświetlane informacje związane z wybranym polem właściwości. Ta funkcja jest domyślnie włączona. Jeśli chcesz ukryć pole opisu, kliknij prawym przyciskiem myszy okno **Właściwości** i kliknij polecenie **Opis**. Spowoduje to również usunięcie znacznika wyboru obok tytułu **opisu** w oknie menu. Pole można wyświetlić ponownie, wykonując te same kroki, aby ponownie włączyć **opis.**

 Informacje w polu opisu <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>pochodzą z pliku . Każda metoda, interfejs, coclass i tak dalej może `helpstring` mieć nieprzydzielony atrybut w bibliotece typów. Okno **Właściwości** pobiera ciąg z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>pliku .

### <a name="to-specify-localized-help-strings"></a>Aby określić zlokalizowane ciągi pomocy

1. Dodaj `helpstringdll` atrybut do instrukcji biblioteki w`typelib`bibliotece typów ( ).

   > [!NOTE]
   > Ten krok jest opcjonalny, jeśli biblioteka typów znajduje się w pliku biblioteki obiektów (olb).

2. Określ `helpstringcontext` atrybuty ciągów. Można również `helpstring` określić atrybuty.

    Atrybuty te różnią `helpfile` `helpcontext` się od atrybutów i, które są zawarte w rzeczywistych tematach Pomocy pliku .chm.

   Aby pobrać informacje o opisie, które mają być **Properties** wyświetlane dla <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> wyróżnionej nazwy właściwości, okno Właściwości `lcid` wywołuje właściwość, która jest zaznaczona, określając żądany atrybut dla ciągu wyjściowego. Wewnętrznie <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> znajduje plik dll określony w `helpstringdll` atrybucie i wywołuje `DLLGetDocumentation` ten plik dll z określonym kontekstem i `lcid` atrybutem.

   Podpisanie i realizacja `DLLGetDocumentation` to:

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

 Funkcja `DLLGetDocumentation` musi być eksport zdefiniowany w pliku def dla biblioteki DLL.

 Wewnętrznie tworzony jest plik olb, który w rzeczywistości jest biblioteką DLL. Ta biblioteka DLL zawiera jeden zasób, plik biblioteki typów `DLLGetDocumentation`(tlb) i jedną wyeksportowane funkcje.

 W przypadku plików olb `helpstringdll` atrybut jest opcjonalny, ponieważ jest to ten sam plik, który zawiera sam plik tlb.

 Aby uzyskać ciągi, aby pokazać się w **opisy** okienka, w związku `helpstring` z tym minimum, co musisz zrobić, to określić atrybut w bibliotece typów. Jeśli chcesz, aby te ciągi były zlokalizowane, musisz określić `helpstringdll` `helpstringcontext` (opcjonalny) atrybut i `DLLGetDocumentation`(wymagany) atrybut i zaimplementować .

 Nie ma żadnych dodatkowych interfejsów, które muszą być zaimplementowane podczas uzyskiwania zlokalizowanych informacji za pośrednictwem atrybutu `helpstringcontext` idl i `DLLGetDocumentation`.

 Innym sposobem uzyskania zlokalizowanej nazwy i opisu właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>jest wdrożenie . Aby uzyskać więcej informacji dotyczących implementacji tej metody, zobacz [Właściwości pola okien i interfejsy](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
