[HTML version](http://htmlpreview.github.io/?https://github.com/idapython/src/blob/master/examples/index.html)

# IDAPython examples

## Category: analysis

#### dump_func_info
<details>
  <summary>dump (some) information about the current function.</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/analysis/dump_func_info.py">analysis/dump_func_info.py</a>

#### Category
analysis

#### Description
Dump some of the most interesting bits of information about
the function we are currently looking at.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_funcs.FUNC_FRAME
* ida_funcs.FUNC_LUMINA
* ida_funcs.FUNC_THUNK
* ida_funcs.get_fchunk
* ida_funcs.is_func_entry
* ida_funcs.is_func_tail
* ida_kernwin.get_screen_ea

</blockquote>

  </details>

## Category: core

#### actions
<details>
  <summary>custom actions, with icons & tooltips</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/actions.py">core/actions.py</a>

#### Category
core

#### Description
How to create user actions, that once created can be
inserted in menus, toolbars, context menus, ...

Those actions, when triggered, will be passed a 'context'
that contains some of the most frequently needed bits of
information.

In addition, custom actions can determine when they want
to be available (through their
`ida_kernwin.action_handler_t.update` callback)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions ctxmenu UI_Hooks

#### Uses
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_DISASM
* ida_kernwin.SETMENU_APP
* ida_kernwin.UI_Hooks
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_menu
* ida_kernwin.attach_action_to_popup
* ida_kernwin.attach_action_to_toolbar
* ida_kernwin.get_widget_type
* ida_kernwin.load_custom_icon
* ida_kernwin.register_action
* ida_kernwin.unregister_action

#### See also
* [add_hotkey](#add_hotkey)

</blockquote>

  </details>

#### add_hotkey
<details>
  <summary>triggering bits of code by pressing a shortcut</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/add_hotkey.py">core/add_hotkey.py</a>

#### Category
core

#### Description
`ida_kernwin.add_hotkey` is a simpler, but much less flexible
alternative to `ida_kernwin.register_action` (though it does
use the same mechanism under the hood.)

It's particularly useful during prototyping, but note that the
actions that are created cannot be inserted in menus, toolbars
or cannot provide a custom `ida_kernwin.action_handler_t.update`
callback.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions

#### Uses
* ida_kernwin.add_hotkey
* ida_kernwin.del_hotkey

#### See also
* [actions](#actions)

</blockquote>

  </details>

#### add_idc_hotkey
<details>
  <summary>triggering bits of code by pressing a shortcut (older version)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/add_idc_hotkey.py">core/add_idc_hotkey.py</a>

#### Category
core

#### Description
This is a somewhat ancient way of registering actions & binding
shortcuts. It's still here for reference, but "fresher" alternatives
should be preferred.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions

#### Uses
* ida_expr.compile_idc_text
* ida_kernwin.add_idc_hotkey

#### See also
* [actions](#actions)
* [add_hotkey](#add_hotkey)

</blockquote>

  </details>

#### auto_instantiate_widget_plugin
<details>
  <summary>better integrating custom widgets in the desktop layout</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/auto_instantiate_widget_plugin.py">core/auto_instantiate_widget_plugin.py</a>

#### Category
core

#### Description
This is an example demonstrating how one can create widgets from a plugin,
and have them re-created automatically at IDA startup-time or at desktop load-time.

This example should be placed in the 'plugins' directory of the
IDA installation, for it to work.

There are 2 ways to use this example:
1) reloading an IDB, where the widget was opened
   - open the widget ('View > Open subview > ...')
   - save this IDB, and close IDA
   - restart IDA with this IDB
     => the widget will be visible

2) reloading a desktop, where the widget was opened
   - open the widget ('View > Open subview > ...')
   - save the desktop ('Windows > Save desktop...') under, say, the name 'with_auto'
   - start another IDA instance with some IDB, and load that desktop
     => the widget will be visible
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
desktop UI_Hooks

#### Uses
* ida_idaapi.plugin_t
* ida_kernwin.AST_ENABLE_ALWAYS
* ida_kernwin.SETMENU_APP
* ida_kernwin.UI_Hooks
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_menu
* ida_kernwin.find_widget
* ida_kernwin.register_action
* ida_kernwin.simplecustviewer_t
* ida_kernwin.simplecustviewer_t.Create

</blockquote>

  </details>

#### bin_search
<details>
  <summary>showcasing `ida_bytes.bin_search`</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/bin_search.py">core/bin_search.py</a>

#### Category
core

#### Description
IDAPython's ida_bytes.bin_search function is pretty powerful,
but can be tough to figure out at first. This example introduces

 * `ida_bytes.bin_search`, and
 * `ida_bytes.parse_binpat_str`

in order to implement a simple replacement for the
'Search > Sequence of bytes...' dialog, that lets users
search for sequences of bytes that compose string literals
in the binary file (either in the default 1-byte-per-char
encoding, or as UTF-16.)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.BIN_SEARCH_FORWARD
* ida_bytes.BIN_SEARCH_NOBREAK
* ida_bytes.BIN_SEARCH_NOSHOW
* ida_bytes.bin_search
* ida_bytes.compiled_binpat_vec_t
* ida_bytes.parse_binpat_str
* ida_ida.inf_get_max_ea
* ida_idaapi.BADADDR
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_DISASM
* ida_kernwin.Form
* ida_kernwin.Form.ChkGroupControl
* ida_kernwin.Form.StringInput
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.get_screen_ea
* ida_kernwin.jumpto
* ida_kernwin.register_action
* ida_nalt.BPU_1B
* ida_nalt.BPU_2B
* ida_nalt.get_default_encoding_idx

</blockquote>

  </details>

#### create_structure_programmatically
<details>
  <summary>programmatically create & populate a structure</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/create_structure_programmatically.py">core/create_structure_programmatically.py</a>

#### Category
core

#### Description
Usage of the API to create & populate a structure with
members of different types.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.FF_BYTE
* ida_bytes.FF_DATA
* ida_bytes.FF_DOUBLE
* ida_bytes.FF_DWORD
* ida_bytes.FF_FLOAT
* ida_bytes.FF_OWORD
* ida_bytes.FF_PACKREAL
* ida_bytes.FF_QWORD
* ida_bytes.FF_STRLIT
* ida_bytes.FF_STRUCT
* ida_bytes.FF_TBYTE
* ida_bytes.FF_WORD
* ida_bytes.off_flag
* ida_bytes.stroff_flag
* ida_idaapi.BADADDR
* ida_nalt.STRTYPE_C
* ida_struct.add_struc
* ida_struct.get_struc_id
* ida_struct.get_struc_size
* idc.add_struc
* idc.add_struc_member
* idc.del_struc
* idc.set_member_type

#### Author
Gergely Erdelyi (gergely.erdelyi@d-dome.net)

</blockquote>

  </details>

#### custom_cli
<details>
  <summary>a custom command-line interpreter</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/custom_cli.py">core/custom_cli.py</a>

#### Category
core

#### Description
Illustrates how one can add command-line interpreters to IDA

This custom interpreter doesn't actually run any code; it's
there as a 'getting started'.
It provides an example tab completion support.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_idaapi.NW_CLOSEIDB
* ida_idaapi.NW_OPENIDB
* ida_idaapi.NW_REMOVE
* ida_idaapi.NW_TERMIDA
* ida_idaapi.notify_when
* ida_kernwin.cli_t

</blockquote>

  </details>

#### custom_data_types_and_formats
<details>
  <summary>using custom data types & printers</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/custom_data_types_and_formats.py">core/custom_data_types_and_formats.py</a>

#### Category
core

#### Description
IDA can be extended to support certain data types that it
does not know about out-of-the-box.

A 'custom data type' provide information about the type &
size of a piece of data, while a 'custom data format' is in
charge of formatting that data (there can be more than
one format for a specific 'custom data type'.)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.data_format_t
* ida_bytes.data_type_t
* ida_bytes.find_custom_data_type
* ida_bytes.get_byte
* ida_bytes.register_data_types_and_formats
* ida_bytes.unregister_data_types_and_formats
* ida_idaapi.NW_CLOSEIDB
* ida_idaapi.NW_OPENIDB
* ida_idaapi.NW_REMOVE
* ida_idaapi.NW_TERMIDA
* ida_idaapi.notify_when
* ida_idaapi.struct_unpack
* ida_lines.COLSTR
* ida_lines.SCOLOR_IMPNAME
* ida_lines.SCOLOR_INSN
* ida_lines.SCOLOR_NUMBER
* ida_lines.SCOLOR_REG
* ida_nalt.get_input_file_path
* ida_netnode.netnode
* ida_struct.is_member_id

</blockquote>

  </details>

#### dump_extra_comments
<details>
  <summary>retrieve extra comments</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/dump_extra_comments.py">core/dump_extra_comments.py</a>

#### Category
core

#### Description
Use the `ida_lines.get_extra_cmt` API to retrieve anterior
and posterior extra comments.

This script registers two actions, that can be used to dump
the previous and next extra comments.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
ctxmenu

#### Uses
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_DISASM
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.find_widget
* ida_kernwin.get_screen_ea
* ida_kernwin.register_action
* ida_kernwin.unregister_action
* ida_lines.E_NEXT
* ida_lines.E_PREV
* ida_lines.get_extra_cmt
* ida_view

</blockquote>

  </details>

#### dump_flowchart
<details>
  <summary>dump function flowchart</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/dump_flowchart.py">core/dump_flowchart.py</a>

#### Category
core

#### Description
Dumps the current function's flowchart, using 2 methods:

  * the low-level `ida_gdl.qflow_chart_t` type
  * the somewhat higher-level, and slightly more pythonic
    `ida_gdl.FlowChart` type.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_funcs.get_func
* ida_gdl.FlowChart
* ida_gdl.qflow_chart_t
* ida_kernwin.get_screen_ea

</blockquote>

  </details>

#### dump_selection
<details>
  <summary>retrieve & dump current selection</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/dump_selection.py">core/dump_selection.py</a>

#### Category
core

#### Description
Shows how to retrieve the selection from a listing
widget ("IDA View-A", "Hex View-1", "Pseudocode-A", ...) as
two "cursors", and from there retrieve (in fact, generate)
the corresponding text.

After running this script:

  * select some text in one of the listing widgets (i.e.,
    "IDA View-*", "Enums", "Structures", "Pseudocode-*")
  * press Ctrl+Shift+S to dump the selection
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_kernwin.ACF_HAS_SELECTION
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_DISASM
* ida_kernwin.BWN_ENUMS
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.BWN_STRUCTS
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.get_viewer_user_data
* ida_kernwin.l_compare2
* ida_kernwin.linearray_t
* ida_kernwin.register_action
* ida_kernwin.unregister_action
* ida_lines.tag_remove

</blockquote>

  </details>

#### extend_idc
<details>
  <summary>add functions to the IDC runtime from IDAPython</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/extend_idc.py">core/extend_idc.py</a>

#### Category
core

#### Description
You can add IDC functions to IDA, whose "body" consists of
IDAPython statements!

We'll register a 'pow' function, available to all IDC code,
that when invoked will call back into IDAPython, and execute
the provided function body.

After running this script, try switching to the IDC interpreter
(using the button on the lower-left corner of IDA) and executing
`pow(3, 7)`
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_expr.VT_LONG
* ida_expr.add_idc_func

</blockquote>

  </details>

#### idapythonrc
<details>
  <summary>code to be run right after IDAPython initialization</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/idapythonrc.py">core/idapythonrc.py</a>

#### Category
core

#### Description
The `idapythonrc.py` file:

  * %APPDATA%\Hex-Rays\IDA Pro\idapythonrc.py (on Windows)
  * ~/.idapro/idapythonrc.py (on Linux & Mac)

can contain any IDAPython code that will be run as soon as
IDAPython is done successfully initializing.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

</blockquote>

  </details>

#### install_user_defined_prefix
<details>
  <summary>inserting information into disassembly prefixes</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/install_user_defined_prefix.py">core/install_user_defined_prefix.py</a>

#### Category
core

#### Description
By default, disassembly line prefixes contain segment + address
information (e.g., '.text:08047718'), but it is possible to
"inject" other bits of information in there, thanks to the
`ida_lines.user_defined_prefix_t` helper type.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_lines.SCOLOR_INV
* ida_lines.user_defined_prefix_t

</blockquote>

  </details>

#### list_imports
<details>
  <summary>enumerate file imports</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_imports.py">core/list_imports.py</a>

#### Category
core

#### Description
Using the API to enumerate file imports.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_nalt.enum_import_names
* ida_nalt.get_import_module_name
* ida_nalt.get_import_module_qty

</blockquote>

  </details>

#### list_patched_bytes
<details>
  <summary>enumerate patched bytes</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_patched_bytes.py">core/list_patched_bytes.py</a>

#### Category
core

#### Description
Using the API to iterate over all the places in the file,
that were patched using IDA.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.visit_patched_bytes
* ida_idaapi.BADADDR

</blockquote>

  </details>

#### list_problems
<details>
  <summary>enumerate problems</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_problems.py">core/list_problems.py</a>

#### Category
core

#### Description
Using the API to list all problem[atic situation]s that IDA
encountered during analysis.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_ida.inf_get_min_ea
* ida_idaapi.BADADDR
* ida_problems.PR_ATTN
* ida_problems.PR_BADSTACK
* ida_problems.PR_COLLISION
* ida_problems.PR_DECIMP
* ida_problems.PR_DISASM
* ida_problems.PR_FINAL
* ida_problems.PR_HEAD
* ida_problems.PR_ILLADDR
* ida_problems.PR_JUMP
* ida_problems.PR_MANYLINES
* ida_problems.PR_NOBASE
* ida_problems.PR_NOCMT
* ida_problems.PR_NOFOP
* ida_problems.PR_NONAME
* ida_problems.PR_NOXREFS
* ida_problems.PR_ROLLED
* ida_problems.get_problem
* ida_problems.get_problem_name

</blockquote>

  </details>

#### list_segment_functions
<details>
  <summary>list all functions (and xrefs) in segment</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_segment_functions.py">core/list_segment_functions.py</a>

#### Category
core

#### Description
List all the functions in the current segment, as well as
all the cross-references to them.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
xrefs

#### Uses
* ida_funcs.get_func
* ida_funcs.get_func_name
* ida_funcs.get_next_func
* ida_idaapi.BADADDR
* ida_kernwin.get_screen_ea
* ida_segment.getseg
* ida_xref.get_first_cref_to
* ida_xref.get_next_cref_to

#### See also
* [list_segment_functions_using_idautils](#list_segment_functions_using_idautils)

</blockquote>

  </details>

#### list_segment_functions_using_idautils
<details>
  <summary>list all functions (and xrefs) in segment</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_segment_functions_using_idautils.py">core/list_segment_functions_using_idautils.py</a>

#### Category
core

#### Description
List all the functions in the current segment, as well as
all the cross-references to them.

Contrary to @list_segment_functions, this uses the somewhat
higher-level `idautils` module.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
xrefs

#### Uses
* ida_funcs.get_func_name
* ida_idaapi.BADADDR
* ida_kernwin.get_screen_ea
* ida_segment.getseg
* idautils.CodeRefsTo
* idautils.Functions

#### See also
* [list_segment_functions](#list_segment_functions)

</blockquote>

  </details>

#### list_stkvar_xrefs
<details>
  <summary>list all xrefs to a function stack variable</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_stkvar_xrefs.py">core/list_stkvar_xrefs.py</a>

#### Category
core

#### Description
Contrary to (in-memory) data & code xrefs, retrieving stack variables
xrefs requires a bit more work than just using ida_xref's first_to(),
next_to() (or higher level utilities such as idautils.XrefsTo)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
xrefs

#### Uses
* ida_bytes.get_flags
* ida_bytes.is_stkvar
* ida_frame.calc_stkvar_struc_offset
* ida_frame.get_frame
* ida_funcs.func_item_iterator_t
* ida_funcs.get_func
* ida_ida.UA_MAXOP
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_DISASM
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.get_current_viewer
* ida_kernwin.get_highlight
* ida_kernwin.get_screen_ea
* ida_kernwin.register_action
* ida_struct.get_member_by_name
* ida_struct.get_struc
* ida_ua.decode_insn
* ida_ua.insn_t

</blockquote>

  </details>

#### list_strings
<details>
  <summary>retrieve the strings that are present in the IDB</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/list_strings.py">core/list_strings.py</a>

#### Category
core

#### Description
This uses `idautils.Strings` to iterate over the string literals
that are present in the IDB. Contrary to @show_selected_strings,
this will not require that the "Strings" window is opened & available.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* idautils.Strings

#### See also
* [show_selected_strings](#show_selected_strings)

</blockquote>

  </details>

#### produce_c_file
<details>
  <summary>decompile entire file</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/produce_c_file.py">core/produce_c_file.py</a>

#### Category
core

#### Description
automate IDA to perform auto-analysis on a file and,
once that is done, produce a .c file containing the
decompilation of all the functions in that file.

Run like so:

      ida -A "-S...path/to/produce_c_file.py" <binary-file>

where:

  * -A instructs IDA to run in non-interactive mode
  * -S holds a path to the script to run (note this is a single token;
       there is no space between '-S' and its path.)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_auto.auto_wait
* ida_hexrays.VDRUN_MAYSTOP
* ida_hexrays.VDRUN_NEWFILE
* ida_hexrays.VDRUN_SILENT
* ida_hexrays.decompile_many
* ida_loader.PATH_TYPE_IDB
* ida_loader.get_path
* ida_pro.qexit

</blockquote>

  </details>

#### produce_lst_file
<details>
  <summary>produce listing</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/produce_lst_file.py">core/produce_lst_file.py</a>

#### Category
core

#### Description
automate IDA to perform auto-analysis on a file and,
once that is done, produce a .lst file with the disassembly.

Run like so:

      ida -A "-S...path/to/produce_lst_file.py" <binary-file>

where:

  * -A instructs IDA to run in non-interactive mode
  * -S holds a path to the script to run (note this is a single token;
       there is no space between '-S' and its path.)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_auto.auto_wait
* ida_fpro.qfile_t
* ida_ida.inf_get_max_ea
* ida_ida.inf_get_min_ea
* ida_loader.OFILE_LST
* ida_loader.PATH_TYPE_IDB
* ida_loader.gen_file
* ida_loader.get_path
* ida_pro.qexit

</blockquote>

  </details>

#### register_timer
<details>
  <summary>using timers for delayed execution</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/register_timer.py">core/register_timer.py</a>

#### Category
core

#### Description
Register (possibly repeating) timers.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_kernwin.register_timer

</blockquote>

  </details>

#### trigger_actions_programmatically
<details>
  <summary>execute existing actions programmatically</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/trigger_actions_programmatically.py">core/trigger_actions_programmatically.py</a>

#### Category
core

#### Description
It's possible to invoke any action programmatically, by using
either of those two:

  * ida_kernwin.execute_ui_requests()
  * ida_kernwin.process_ui_action()

Ideally, this script should be run through the "File > Script file..."
menu, so as to keep focus on "IDA View-A" and have the
'ProcessUiActions' part work as intended.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions

#### Uses
* ida_kernwin.ask_yn
* ida_kernwin.execute_ui_requests
* ida_kernwin.msg
* ida_kernwin.process_ui_action

</blockquote>

  </details>

## Category: debugging

#### automatic_steps
<details>
  <summary>programmatically drive a debugging session</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/dbghooks/automatic_steps.py">debugging/dbghooks/automatic_steps.py</a>

#### Category
debugging

#### Description
Start a debugging session, step through the first five
instructions. Each instruction is disassembled after
execution.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
DBG_Hooks

#### Uses
* ida_dbg.DBG_Hooks
* ida_dbg.get_reg_val
* ida_dbg.request_exit_process
* ida_dbg.request_run_to
* ida_dbg.request_step_over
* ida_dbg.run_requests
* ida_ida.inf_get_start_ip
* ida_idaapi.BADADDR
* ida_lines.generate_disasm_line
* ida_lines.tag_remove

</blockquote>

  </details>

#### dbg_trace
<details>
  <summary>using the low-level tracing hook</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/dbghooks/dbg_trace.py">debugging/dbghooks/dbg_trace.py</a>

#### Category
debugging

#### Description
This script demonstrates using the low-level tracing hook
(ida_dbg.DBG_Hooks.dbg_trace). It can be run like so:

     ida[t].exe -B -Sdbg_trace.py -Ltrace.log file.exe
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
DBG_Hooks

#### Uses
* GENDSM_FORCE_CODE
* GENDSM_REMOVE_TAGS
* NN_call
* NN_callfi
* NN_callni
* generate_disasm_line
* ida_dbg.DBG_Hooks
* ida_dbg.ST_OVER_DEBUG_SEG
* ida_dbg.ST_OVER_LIB_FUNC
* ida_dbg.enable_step_trace
* ida_dbg.get_process_state
* ida_dbg.get_reg_val
* ida_dbg.get_step_trace_options
* ida_dbg.load_debugger
* ida_dbg.refresh_debugger_memory
* ida_dbg.request_continue_process
* ida_dbg.request_enable_step_trace
* ida_dbg.request_set_step_trace_options
* ida_dbg.run_requests
* ida_dbg.run_to
* ida_dbg.set_step_trace_options
* ida_dbg.wait_for_next_event
* ida_ida.f_ELF
* ida_ida.f_MACHO
* ida_ida.f_PE
* ida_ida.inf_get_filetype
* ida_ida.inf_get_max_ea
* ida_ida.inf_get_min_ea
* ida_ida.inf_get_start_ip
* ida_pro.qexit
* ida_ua.decode_insn
* ida_ua.insn_t
* idc.ARGV

</blockquote>

  </details>

#### registers_context_menu
<details>
  <summary>adding actions to the "registers" widget(s)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/misc/registers_context_menu.py">debugging/misc/registers_context_menu.py</a>

#### Category
debugging

#### Description
It's possible to add actions to the context menu of
pretty much all widgets in IDA.

This example shows how to do just that for
registers-displaying widgets (e.g., "General registers")
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
ctxmenu UI_Hooks

#### Uses
* ida_dbg.get_dbg_reg_info
* ida_dbg.get_reg_val
* ida_idd.register_info_t
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_CPUREGS
* ida_kernwin.UI_Hooks
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.get_widget_type
* ida_kernwin.register_action
* ida_ua.dt_byte
* ida_ua.dt_dword
* ida_ua.dt_qword
* ida_ua.dt_word

</blockquote>

  </details>

#### show_debug_names
<details>
  <summary>retrieving & dumping debuggee symbols</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/show_debug_names.py">debugging/show_debug_names.py</a>

#### Category
debugging

#### Description
Queries the debugger (possibly remotely) for the list of
symbols that the process being debugged, provides.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_dbg.get_process_state
* ida_dbg.is_debugger_on
* ida_ida.inf_get_max_ea
* ida_ida.inf_get_min_ea
* ida_name.get_debug_names

</blockquote>

  </details>

#### simple_appcall_common
<details>
  <summary></summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/appcall/simple_appcall_common.py">debugging/appcall/simple_appcall_common.py</a>

#### Category
debugging

#### Description

And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
DBG_Hooks

#### Uses
* ida_dbg.DBG_Hooks
* ida_dbg.run_to
* ida_idaapi.BADADDR
* ida_idd.Appcall
* ida_idd.Appcall.byref
* ida_idd.Appcall.int64
* ida_kernwin.get_screen_ea
* ida_name.get_name_ea
* ida_name.set_name
* ida_typeinf.apply_cdecl

</blockquote>

  </details>

#### simple_appcall_linux
<details>
  <summary>executing code into the application being debugged (on Linux)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/appcall/simple_appcall_linux.py">debugging/appcall/simple_appcall_linux.py</a>

#### Category
debugging

#### Description
Using the `ida_idd.Appcall` utility to execute code in
the process being debugged.

This example will run the test program and stop wherever
the cursor currently is, and then perform an appcall to
execute the `ref4` and `ref8` functions.

To use this example:

  * run `ida64` on test program `simple_appcall_linux64`, or
    `ida` on test program `simple_appcall_linux32`, and wait for
    auto-analysis to finish
  * select the 'linux debugger' (either local, or remote)
  * run this script

Note: the real body of code is in `simple_appcall_common.py`.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

</blockquote>

  </details>

#### simple_appcall_win
<details>
  <summary>executing code into the application being debugged (on Windows)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/debugging/appcall/simple_appcall_win.py">debugging/appcall/simple_appcall_win.py</a>

#### Category
debugging

#### Description
Using the `ida_idd.Appcall` utility to execute code in
the process being debugged.

This example will run the test program and stop wherever
the cursor currently is, and then perform an appcall to
execute the `ref4` and `ref8` functions.

To use this example:

  * run `ida64` on test program `simple_appcall_win64.exe`, or
    `ida` on test program `simple_appcall_win32.exe`, and wait for
    auto-analysis to finish
  * select the 'windows debugger' (either local, or remote)
  * run this script

Note: the real body of code is in `simple_appcall_common.py`.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_ida.inf_is_64bit

</blockquote>

  </details>

## Category: disassembly

#### colorize_disassembly
<details>
  <summary>change background colours</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/core/colorize_disassembly.py">core/colorize_disassembly.py</a>

#### Category
disassembly

#### Description
This illustrates the setting/retrieval of background colours
using the IDC wrappers
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
coloring idc

#### Uses
* idc.CIC_FUNC
* idc.CIC_ITEM
* idc.CIC_SEGM
* idc.get_color
* idc.here
* idc.set_color

</blockquote>

  </details>

## Category: hexrays

#### colorize_pseudocode_lines
<details>
  <summary>interactively color certain pseudocode lines</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/colorize_pseudocode_lines.py">hexrays/colorize_pseudocode_lines.py</a>

#### Category
hexrays

#### Description
Provides an action that can be used to dynamically alter the
lines background rendering for pseudocode listings (as opposed to
using `ida_hexrays.cfunc_t.pseudocode[N].bgcolor`)

After running this script, pressing 'M' on a line in a
"Pseudocode-?" widget, will cause that line to be rendered
with a special background color.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
colors UI_Hooks

#### Uses
* ida_hexrays.get_widget_vdui
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.CK_EXTRA11
* ida_kernwin.UI_Hooks
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.get_custom_viewer_location
* ida_kernwin.line_rendering_output_entry_t
* ida_kernwin.refresh_custom_viewer
* ida_kernwin.register_action
* ida_moves.lochist_entry_t

</blockquote>

  </details>

#### decompile_entry_points
<details>
  <summary>automatic decompilation of functions</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/decompile_entry_points.py">hexrays/decompile_entry_points.py</a>

#### Category
hexrays

#### Description
Attempts to load a decompiler plugin corresponding to the current
architecture (and address size) right after auto-analysis is performed,
and then tries to decompile the function at the first entrypoint.

It is particularly suited for use with the '-S' flag, for example:
idat -Ldecompile.log -Sdecompile_entry_points.py -c file
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_auto.auto_wait
* ida_entry.get_entry
* ida_entry.get_entry_ordinal
* ida_entry.get_entry_qty
* ida_hexrays.decompile
* ida_hexrays.init_hexrays_plugin
* ida_ida.inf_is_64bit
* ida_idp.PLFM_386
* ida_idp.PLFM_ARM
* ida_idp.PLFM_MIPS
* ida_idp.PLFM_PPC
* ida_idp.ph.id
* ida_kernwin.cvar.batch
* ida_kernwin.msg
* ida_loader.load_plugin
* ida_pro.qexit
* idc.get_idb_path

</blockquote>

  </details>

#### vds1
<details>
  <summary>decompile & print current function.</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds1.py">hexrays/vds1.py</a>

#### Category
hexrays

#### Description
decompile & print current function.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_funcs.get_func
* ida_hexrays.decompile
* ida_hexrays.get_hexrays_version
* ida_hexrays.init_hexrays_plugin
* ida_kernwin.get_screen_ea
* ida_lines.tag_remove

</blockquote>

  </details>

#### vds10
<details>
  <summary>a custom microcode instruction optimization rule</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds10.py">hexrays/vds10.py</a>

#### Category
hexrays

#### Description
Installs a custom microcode instruction optimization rule,
to transform:

    call   !DbgRaiseAssertionFailure <fast:>.0

into

    call   !DbgRaiseAssertionFailure <fast:"char *" "assertion text">.0

To see this plugin in action please use arm64_brk.i64
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.get_cmt
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.mop_str
* ida_hexrays.optinsn_t
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_typeinf.STI_PCCHAR
* ida_typeinf.tinfo_t.get_stock

</blockquote>

  </details>

#### vds11
<details>
  <summary>a custom microcode block optimization rule (resolve `goto` chains)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds11.py">hexrays/vds11.py</a>

#### Category
hexrays

#### Description
Installs a custom microcode block optimization rule,
to transform:

      goto L1
      ...
    L1:
      goto L2

into

      goto L2

In other words we fix a goto target if it points to a chain of gotos.
This improves the decompiler output in some cases.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_hexrays.getf_reginsn
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.m_goto
* ida_hexrays.optblock_t
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t

</blockquote>

  </details>

#### vds12
<details>
  <summary>list instruction registers</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds12.py">hexrays/vds12.py</a>

#### Category
hexrays

#### Description
Shows a list of direct references to a register from the
current instruction.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.get_flags
* ida_bytes.is_code
* ida_funcs.get_func
* ida_hexrays.ACFL_GUESS
* ida_hexrays.DECOMP_NO_CACHE
* ida_hexrays.DECOMP_WARNINGS
* ida_hexrays.GCO_DEF
* ida_hexrays.GCO_USE
* ida_hexrays.GC_REGS_AND_STKVARS
* ida_hexrays.MERR_OK
* ida_hexrays.MMAT_PREOPTIMIZED
* ida_hexrays.MUST_ACCESS
* ida_hexrays.gco_info_t
* ida_hexrays.gen_microcode
* ida_hexrays.get_current_operand
* ida_hexrays.get_merror_desc
* ida_hexrays.hexrays_failure_t
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.mba_ranges_t
* ida_hexrays.mlist_t
* ida_hexrays.op_parent_info_t
* ida_hexrays.voff_t
* ida_kernwin.Choose
* ida_kernwin.get_screen_ea
* ida_kernwin.jumpto
* ida_kernwin.warning
* ida_lines.GENDSM_REMOVE_TAGS
* ida_lines.generate_disasm_line
* ida_pro.eavec_t

</blockquote>

  </details>

#### vds13
<details>
  <summary>generates microcode for selection</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds13.py">hexrays/vds13.py</a>

#### Category
hexrays

#### Description
Generates microcode for selection and dumps it to the output window.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.get_flags
* ida_bytes.is_code
* ida_hexrays.DECOMP_WARNINGS
* ida_hexrays.gen_microcode
* ida_hexrays.hexrays_failure_t
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.mba_ranges_t
* ida_hexrays.vd_printer_t
* ida_kernwin.read_range_selection
* ida_kernwin.warning
* ida_range.range_t

</blockquote>

  </details>

#### vds17
<details>
  <summary>using the "Select offsets" widget</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds17.py">hexrays/vds17.py</a>

#### Category
hexrays

#### Description
Registers an action opens the "Select offsets" widget
(select_udt_by_offset() call).

This effectively repeats the functionality already available
through Alt+Y.

Place cursor on the union field and press Shift+T
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_hexrays.USE_KEYBOARD
* ida_hexrays.cot_add
* ida_hexrays.cot_cast
* ida_hexrays.cot_memptr
* ida_hexrays.cot_memref
* ida_hexrays.cot_num
* ida_hexrays.cot_ref
* ida_hexrays.get_hexrays_version
* ida_hexrays.get_widget_vdui
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.select_udt_by_offset
* ida_hexrays.ui_stroff_applicator_t
* ida_hexrays.ui_stroff_ops_t
* ida_idaapi.BADADDR
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.get_custom_viewer_curline
* ida_kernwin.msg
* ida_kernwin.register_action
* ida_kernwin.warning
* ida_lines.tag_remove
* ida_typeinf.PRTYPE_1LINE
* ida_typeinf.print_tinfo
* ida_typeinf.remove_pointer

</blockquote>

  </details>

#### vds19
<details>
  <summary>a custom microcode instruction optimization rule (`x | ~x => -1`)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds19.py">hexrays/vds19.py</a>

#### Category
hexrays

#### Description
Installs a custom microcode instruction optimization rule,
to transform:

    x | ~x

into

    -1

To see this plugin in action please use be_ornot_be.idb
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.m_bnot
* ida_hexrays.m_mov
* ida_hexrays.m_or
* ida_hexrays.minsn_visitor_t
* ida_hexrays.mop_t
* ida_hexrays.optinsn_t
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t

</blockquote>

  </details>

#### vds21
<details>
  <summary>dynamically provide a custom call type</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds21.py">hexrays/vds21.py</a>

#### Category
hexrays

#### Description
This plugin can greatly improve decompilation of indirect calls:

    call    [eax+4]

For them, the decompiler has to guess the prototype of the called function.
This has to be done at a very early phase of decompilation because
the function prototype influences the data flow analysis. On the other
hand, we do not have global data flow analysis results yet because
we haven't analyzed all calls in the function. It is a chicked-and-egg
problem.

The decompiler uses various techniques to guess the called function
prototype. While it works very well, it may fail in some cases.

To fix, the user can specify the call prototype manually, using
"Edit, Operand types, Set operand type" at the call instruction.

This plugin illustrates another approach to the problem:
if you happen to be able to calculate the call prototypes dynamically,
this is how to inform the decompiler about them.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
Hexrays_Hooks

#### Uses
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.m_call
* ida_hexrays.mcallinfo_t
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_kernwin.msg
* ida_kernwin.warning
* ida_nalt.get_op_tinfo
* ida_typeinf.BT_INT
* ida_typeinf.CM_CC_STDCALL
* ida_typeinf.CM_N32_F48
* ida_typeinf.parse_decl
* ida_typeinf.tinfo_t

</blockquote>

  </details>

#### vds3
<details>
  <summary>invert if/else blocks</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds3.py">hexrays/vds3.py</a>

#### Category
hexrays

#### Description
Registers an action that can be used to invert the `if`
and `else` blocks of a `ida_hexrays.cif_t`.

For example, a statement like

    if ( cond )
    {
      statements1;
    }
    else
    {
      statements2;
    }

will be displayed as

    if ( !cond )
    {
      statements2;
    }
    else
    {
      statements1;
    }

The modifications are persistent: the user can quit & restart
IDA, and the changes will be present.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
ctxmenu Hexrays_Hooks

#### Uses
* ida_hexrays.CMAT_FINAL
* ida_hexrays.CV_FAST
* ida_hexrays.CV_INSNS
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.ITP_ELSE
* ida_hexrays.USE_KEYBOARD
* ida_hexrays.VDI_TAIL
* ida_hexrays.cexpr_t
* ida_hexrays.cit_if
* ida_hexrays.ctree_visitor_t
* ida_hexrays.get_widget_vdui
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.lnot
* ida_hexrays.qswap
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.register_action
* ida_netnode.netnode

#### Author
EiNSTeiN_ (einstein@g3nius.org)

</blockquote>

  </details>

#### vds4
<details>
  <summary>dump user-defined information</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds4.py">hexrays/vds4.py</a>

#### Category
hexrays

#### Description
Prints user-defined information to the "Output" window.
Namely:

  * user defined label names
  * user defined indented comments
  * user defined number formats
  * user defined local variable names, types, comments
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_bytes.get_radix
* ida_hexrays.CIT_COLLAPSED
* ida_hexrays.decompile
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.lvar_uservec_t
* ida_hexrays.restore_user_cmts
* ida_hexrays.restore_user_iflags
* ida_hexrays.restore_user_labels
* ida_hexrays.restore_user_lvar_settings
* ida_hexrays.restore_user_numforms
* ida_hexrays.user_cmts_free
* ida_hexrays.user_iflags_free
* ida_hexrays.user_labels_free
* ida_hexrays.user_numforms_free
* ida_kernwin.get_screen_ea

#### Author
EiNSTeiN_ (einstein@g3nius.org)

</blockquote>

  </details>

#### vds5
<details>
  <summary>show ctree graph</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds5.py">hexrays/vds5.py</a>

#### Category
hexrays

#### Description
Registers an action that can be used to show the graph of the ctree.
The current item will be highlighted in the graph.

The command shortcut is `Ctrl+Shift+G`, and is also added
to the context menu.

To display the graph, we produce a .gdl file, and
request that ida displays that using `ida_gdl.display_gdl`.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
ctxmenu Hexrays_Hooks

#### Uses
* ida_gdl.display_gdl
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.USE_KEYBOARD
* ida_hexrays.cit_asm
* ida_hexrays.cit_goto
* ida_hexrays.cot_helper
* ida_hexrays.cot_memptr
* ida_hexrays.cot_memref
* ida_hexrays.cot_num
* ida_hexrays.cot_obj
* ida_hexrays.cot_ptr
* ida_hexrays.cot_str
* ida_hexrays.cot_var
* ida_hexrays.ctree_parentee_t
* ida_hexrays.get_ctype_name
* ida_hexrays.get_widget_vdui
* ida_hexrays.init_hexrays_plugin
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.register_action
* ida_kernwin.warning
* ida_lines.tag_remove
* ida_pro.str2user

</blockquote>

  </details>

#### vds6
<details>
  <summary>superficially modify the decompilation output</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds6.py">hexrays/vds6.py</a>

#### Category
hexrays

#### Description
modifies the decompilation output in a superficial manner,
by removing some white spaces

Note: this is rather crude, not quite "pythonic" code.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
Hexrays_Hooks

#### Uses
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.init_hexrays_plugin
* ida_idaapi.PLUGIN_HIDE
* ida_idaapi.PLUGIN_KEEP
* ida_idaapi.plugin_t
* ida_lines.tag_advance
* ida_lines.tag_skipcodes

</blockquote>

  </details>

#### vds7
<details>
  <summary>iterate a cblock_t object</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds7.py">hexrays/vds7.py</a>

#### Category
hexrays

#### Description
Using a `ida_hexrays.ctree_visitor_t`, search for
`ida_hexrays.cit_block` instances and dump them.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
Hexrays_Hooks

#### Uses
* ida_hexrays.CMAT_BUILT
* ida_hexrays.CV_FAST
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.cit_block
* ida_hexrays.ctree_visitor_t
* ida_hexrays.init_hexrays_plugin

#### Author
EiNSTeiN_ (einstein@g3nius.org)

</blockquote>

  </details>

#### vds8
<details>
  <summary>using `ida_hexrays.udc_filter_t`</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds8.py">hexrays/vds8.py</a>

#### Category
hexrays

#### Description
Registers an action that uses a `ida_hexrays.udc_filter_t` to decompile
`svc 0x900001` and `svc 0x9000F8` as function calls to
`svc_exit()` and `svc_exit_group()` respectively.

You will need to have an ARM + Linux IDB for this script to be usable

In addition to having a shortcut, the action will be present
in the context menu.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
ctxmenu UI_Hooks

#### Uses
* ida_allins.ARM_svc
* ida_hexrays.get_widget_vdui
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.install_microcode_filter
* ida_hexrays.udc_filter_t
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.UI_Hooks
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.get_widget_type
* ida_kernwin.register_action

</blockquote>

  </details>

#### vds_create_hint
<details>
  <summary>decompiler hints</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds_create_hint.py">hexrays/vds_create_hint.py</a>

#### Category
hexrays

#### Description
Handle `ida_hexrays.hxe_create_hint` notification using hooks,
to return our own.

If the object under the cursor is:

* a function call, prefix the original decompiler hint with `==> `
* a local variable declaration, replace the hint with our own in
  the form of `!{varname}` (where `{varname}` is replaced with the
  variable name)
* an `if` statement, replace the hint with our own, saying "condition"
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
Hexrays_Hooks

#### Uses
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.USE_MOUSE
* ida_hexrays.VDI_EXPR
* ida_hexrays.VDI_LVAR
* ida_hexrays.cit_if
* ida_hexrays.cot_call

</blockquote>

  </details>

#### vds_hooks
<details>
  <summary>various decompiler hooks</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds_hooks.py">hexrays/vds_hooks.py</a>

#### Category
hexrays

#### Description
Shows how to hook to many notifications sent by the decompiler.

This plugin doesn't really accomplish anything: it just prints
the parameters.

The list of notifications handled below should be exhaustive,
and is there to hint at what is possible to accomplish by
subclassing `ida_hexrays.Hexrays_Hooks`
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
Hexrays_Hooks

#### Uses
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.cfunc_t
* ida_hexrays.lvar_t
* ida_hexrays.vdui_t

</blockquote>

  </details>

#### vds_modify_user_lvars
<details>
  <summary>modifying local variables</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds_modify_user_lvars.py">hexrays/vds_modify_user_lvars.py</a>

#### Category
hexrays

#### Description
Use a `ida_hexrays.user_lvar_modifier_t` to modify names,
comments and/or types of local variables.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_hexrays.modify_user_lvars
* ida_hexrays.user_lvar_modifier_t
* ida_typeinf.parse_decl
* ida_typeinf.tinfo_t
* idc.here

</blockquote>

  </details>

#### vds_xrefs
<details>
  <summary>show decompiler xrefs</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/hexrays/vds_xrefs.py">hexrays/vds_xrefs.py</a>

#### Category
hexrays

#### Description
Show decompiler-style Xref when the `Ctrl+X` key is
pressed in the Decompiler window.

* supports any global name: functions, strings, integers, ...
* supports structure member.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
ctxmenu Hexrays_Hooks

#### Uses
* ida_funcs.get_func_name
* ida_hexrays.Hexrays_Hooks
* ida_hexrays.USE_KEYBOARD
* ida_hexrays.VDI_EXPR
* ida_hexrays.VDI_FUNC
* ida_hexrays.cexpr_t
* ida_hexrays.cfunc_t
* ida_hexrays.cinsn_t
* ida_hexrays.decompile
* ida_hexrays.get_widget_vdui
* ida_hexrays.init_hexrays_plugin
* ida_hexrays.open_pseudocode
* ida_hexrays.qstring_printer_t
* ida_idaapi.BADADDR
* ida_kernwin.AST_DISABLE
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.PluginForm
* ida_kernwin.PluginForm.Show
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.register_action
* ida_struct.get_member
* ida_struct.get_struc
* ida_struct.get_struc_id
* ida_typeinf.PRTYPE_1LINE
* ida_typeinf.print_tinfo
* idautils.Functions
* idautils.XrefsTo

#### Author
EiNSTeiN_ (einstein@g3nius.org)

</blockquote>

  </details>

## Category: idbhooks

#### operand_changed
<details>
  <summary>notify the user when an instruction operand changes</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/idbhooks/operand_changed.py">idbhooks/operand_changed.py</a>

#### Category
idbhooks

#### Description
Show notifications whenever the user changes
an instruction's operand, or a data item.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
IDB_Hooks

#### Uses
* ida_bytes.ALOPT_IGNCLT
* ida_bytes.ALOPT_IGNHEADS
* ida_bytes.get_flags
* ida_bytes.get_max_strlit_length
* ida_bytes.get_opinfo
* ida_bytes.get_strlit_contents
* ida_bytes.is_custfmt
* ida_bytes.is_custom
* ida_bytes.is_enum
* ida_bytes.is_off
* ida_bytes.is_strlit
* ida_bytes.is_stroff
* ida_bytes.is_struct
* ida_enum.get_enum_name
* ida_idp.IDB_Hooks
* ida_nalt.STRENC_DEFAULT
* ida_nalt.get_default_encoding_idx
* ida_nalt.get_encoding_name
* ida_nalt.get_str_encoding_idx
* ida_nalt.get_strtype_bpu
* ida_nalt.opinfo_t
* ida_struct.get_struc_name

</blockquote>

  </details>

#### replay_prototypes_changes
<details>
  <summary>Record and replay changes in function prototypes</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/idbhooks/replay_prototypes_changes.py">idbhooks/replay_prototypes_changes.py</a>

#### Category
idbhooks

#### Description
This is a sample script, that will record (in memory) all changes in
functions prototypes, in order to re-apply them later.

To use this script:
 - open an IDB (say, "test.idb")
 - modify some functions prototypes (e.g., by triggering the 'Y'
   shortcut when the cursor is placed on the first address of a
   function)
 - reload that IDB, *without saving it first*
 - call rpc.replay(), to re-apply the modifications.

Note: 'ti_changed' is also called for changes to the function
frames, but we'll only record function prototypes changes.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
IDB_Hooks

#### Uses
* ida_funcs.get_func
* ida_idp.IDB_Hooks
* ida_typeinf.PRTYPE_1LINE
* ida_typeinf.TINFO_DEFINITE
* ida_typeinf.apply_tinfo
* ida_typeinf.get_idati
* ida_typeinf.tinfo_t

</blockquote>

  </details>

## Category: idphooks

#### ana_emu_out
<details>
  <summary>override some parts of the processor module</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/idphooks/ana_emu_out.py">idphooks/ana_emu_out.py</a>

#### Category
idphooks

#### Description
Implements disassembly of BUG_INSTR used in Linux kernel
BUG() macro, which is architecturally undefined and is not
disassembled by IDA's ARM module

See Linux/arch/arm/include/asm/bug.h for more info
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
IDP_Hooks

#### Uses
* ida_bytes.get_wide_dword
* ida_bytes.get_wide_word
* ida_idp.CUSTOM_INSN_ITYPE
* ida_idp.IDP_Hooks
* ida_idp.PLFM_ARM
* ida_idp.ph.id
* ida_idp.str2reg
* ida_segregs.get_sreg

</blockquote>

  </details>

#### assemble
<details>
  <summary>an `ida_idp.IDP_Hooks.assembly` implementation</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/idphooks/assemble.py">idphooks/assemble.py</a>

#### Category
idphooks

#### Description
We add support for assembling the following pseudo instructions:

* "zero eax" -> xor eax, eax
* "nothing" -> nop
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
IDP_Hooks

#### Uses
* ida_idp.IDP_Hooks
* idautils.DecodeInstruction

</blockquote>

  </details>

## Category: pyqt

#### inject_command
<details>
  <summary>injecting commands is the "Output" window</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/pyqt/inject_command.py">pyqt/inject_command.py</a>

#### Category
pyqt

#### Description
This example illustrates how one can execute commands in the
"Output" window, from their own widgets.

A few notes:

* the original, underlying `cli:Execute` action, that has to be
  triggered for the code present in the input field to execute
  and be placed in the history, requires that the input field
  has focus (otherwise it simply won't do anything.)
* this, in turn, forces us to do "delayed" execution of that action,
  hence the need for a `QTimer`
* the IDA/SWiG 'TWidget' type that we retrieve through
  `ida_kernwin.find_widget`, is not the same type as a
  `QtWidgets.QWidget`. We therefore need to convert it using
  `ida_kernwin.PluginForm.TWidgetToPyQtWidget`
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_kernwin.PluginForm.TWidgetToPyQtWidget
* ida_kernwin.disabled_script_timeout_t
* ida_kernwin.find_widget
* ida_kernwin.process_ui_action

</blockquote>

  </details>

#### paint_over_navbar
<details>
  <summary>custom painting on top of the navigation band</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/pyqt/paint_over_navbar.py">pyqt/paint_over_navbar.py</a>

#### Category
pyqt

#### Description
Using an "event filter", we'll intercept paint events
targeted at the navigation band widget, let it paint itself,
and then add our own markers on top.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_kernwin.PluginForm.FormToPyQtWidget
* ida_kernwin.get_navband_pixel
* ida_kernwin.open_navband_window
* ida_segment.get_segm_qty
* ida_segment.getnseg
* idc.here

</blockquote>

  </details>

#### populate_pluginform_with_pyqt_widgets
<details>
  <summary>adding PyQt5 widgets into an `ida_kernwin.PluginForm`</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/pyqt/populate_pluginform_with_pyqt_widgets.py">pyqt/populate_pluginform_with_pyqt_widgets.py</a>

#### Category
pyqt

#### Description
Using `ida_kernwin.PluginForm.FormToPyQtWidget`, this script
converts IDA's own dockable widget into a type that is
recognized by PyQt5, which then enables populating it with
regular Qt widgets.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Uses
* ida_kernwin.PluginForm

</blockquote>

  </details>

## Category: uihooks

#### func_chooser_coloring
<details>
  <summary>using `ida_kernwin.UI_Hooks.get_chooser_item_attrs` to override some defaults</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/uihooks/func_chooser_coloring.py">uihooks/func_chooser_coloring.py</a>

#### Category
uihooks

#### Description
color the function in the Function window according to its size.
The larger the function, the darker the color.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
UI_Hooks

#### Uses
* ida_funcs.get_func
* ida_kernwin.UI_Hooks
* ida_kernwin.enable_chooser_item_attrs

</blockquote>

  </details>

#### lines_rendering
<details>
  <summary>dynamically colorize lines backgrounds (or parts of them)</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/uihooks/lines_rendering.py">uihooks/lines_rendering.py</a>

#### Category
uihooks

#### Description
shows how one can dynamically alter the lines background
rendering (as opposed to, say, using ida_nalt.set_item_color()),
and also shows how that rendering can be limited to just a few
glyphs, not the whole line.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
UI_Hooks

#### Uses
* ida_bytes.next_head
* ida_idaapi.BADADDR
* ida_kernwin.CK_EXTRA1
* ida_kernwin.CK_EXTRA10
* ida_kernwin.CK_EXTRA11
* ida_kernwin.CK_EXTRA12
* ida_kernwin.CK_EXTRA13
* ida_kernwin.CK_EXTRA14
* ida_kernwin.CK_EXTRA15
* ida_kernwin.CK_EXTRA16
* ida_kernwin.CK_EXTRA2
* ida_kernwin.CK_EXTRA3
* ida_kernwin.CK_EXTRA4
* ida_kernwin.CK_EXTRA5
* ida_kernwin.CK_EXTRA6
* ida_kernwin.CK_EXTRA7
* ida_kernwin.CK_EXTRA8
* ida_kernwin.CK_EXTRA9
* ida_kernwin.CK_TRACE
* ida_kernwin.CK_TRACE_OVL
* ida_kernwin.LROEF_CPS_RANGE
* ida_kernwin.UI_Hooks
* ida_kernwin.get_screen_ea
* ida_kernwin.line_rendering_output_entry_t
* ida_kernwin.refresh_idaview_anyway

</blockquote>

  </details>

#### log_misc_events
<details>
  <summary>being notified, and logging a few UI events</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/uihooks/log_misc_events.py">uihooks/log_misc_events.py</a>

#### Category
uihooks

#### Description
hooks to be notified about certain UI events, and
dump their information to the "Output" window
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
UI_Hooks

#### Uses
* ida_kernwin.UI_Hooks

</blockquote>

  </details>

#### prevent_jump
<details>
  <summary>taking precedence over actions</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/uihooks/prevent_jump.py">uihooks/prevent_jump.py</a>

#### Category
uihooks

#### Description
Using `ida_kernwin.UI_Hooks.preprocess_action`, it is possible
to respond to a command instead of the action that would
otherwise do it.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
UI_Hooks

#### Uses
* ida_kernwin.UI_Hooks

</blockquote>

  </details>

## Category: widgets

#### add_menus
<details>
  <summary>adding custom menus to IDA</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/misc/add_menus.py">widgets/misc/add_menus.py</a>

#### Category
widgets

#### Description
It is possible to add custom menus to IDA, either at the
toplevel (i.e., into the menubar), or as submenus of existing
menus.

Notes:

  * the same action can be present in more than 1 menu
  * this example does not deal with context menus
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions

#### Uses
* ida_kernwin.AST_ENABLE_ALWAYS
* ida_kernwin.SETMENU_INS
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_menu
* ida_kernwin.create_menu
* ida_kernwin.register_action

</blockquote>

  </details>

#### askusingform
<details>
  <summary>Non-trivial uses of the `ida_kernwin.Form` helper class</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/forms/askusingform.py">widgets/forms/askusingform.py</a>

#### Category
widgets

#### Description
How to query for complex user input, using IDA's built-in forms.

Note: while this example produces full-fledged forms for complex input,
simpler types of inputs might can be retrieved by using
`ida_kernwin.ask_str` and similar functions.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
forms

#### Uses
* ida_kernwin.Choose
* ida_kernwin.Choose.CH_MULTI
* ida_kernwin.Form
* ida_kernwin.PluginForm.FORM_TAB
* ida_kernwin.ask_str

</blockquote>

  </details>

#### choose
<details>
  <summary>A widget showing data in a tabular fashion</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/tabular_views/custom/choose.py">widgets/tabular_views/custom/choose.py</a>

#### Category
widgets

#### Description
Shows how to subclass the ida_kernwin.Choose class to
show data organized in a simple table.
In addition, registers a couple actions that can be applied to it.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions chooser ctxmenu

#### Uses
* Choose
* Choose.ALL_CHANGED
* Choose.CH_CAN_DEL
* Choose.CH_CAN_EDIT
* Choose.CH_CAN_INS
* Choose.CH_CAN_REFRESH
* Choose.CH_RESTORE
* Choose.NOTHING_CHANGED
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.is_chooser_widget
* ida_kernwin.register_action
* ida_kernwin.unregister_action

#### See also
* [choose_multi](#choose_multi)
* [chooser_with_folders](#chooser_with_folders)

</blockquote>

  </details>

#### choose_multi
<details>
  <summary>A widget showing data in a tabular fashion, providing multiple selection</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/tabular_views/custom/choose_multi.py">widgets/tabular_views/custom/choose_multi.py</a>

#### Category
widgets

#### Description
Similar to @{choose}, but with multiple selection
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions chooser

#### Uses
* Choose
* Choose.ALL_CHANGED
* Choose.CHCOL_HEX
* Choose.CH_MULTI
* Choose.NOTHING_CHANGED

#### See also
* [choose](#choose)
* [chooser_with_folders](#chooser_with_folders)

</blockquote>

  </details>

#### chooser_with_folders
<details>
  <summary>A widget that can show tabular data either as a simple table, or with a tree-like structure.</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/tabular_views/custom/chooser_with_folders.py">widgets/tabular_views/custom/chooser_with_folders.py</a>

#### Category
widgets

#### Description
By adding the necessary bits to a ida_kernwin.Choose subclass,
IDA can show the otherwise tabular data, in a tree-like fashion.

The important bits to enable this are:

  * ida_dirtree.dirspec_t (and my_dirspec_t)
  * ida_kernwin.CH_HAS_DIRTREE
  * ida_kernwin.Choose.OnGetDirTree
  * ida_kernwin.Choose.OnIndexToInode
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions chooser folders

#### Uses
* ida_dirtree.DTE_OK
* ida_dirtree.direntry_t
* ida_dirtree.direntry_t.BADIDX
* ida_dirtree.dirspec_t
* ida_dirtree.dirtree_t
* ida_dirtree.dirtree_t.isdir
* ida_kernwin.CH_CAN_DEL
* ida_kernwin.CH_CAN_EDIT
* ida_kernwin.CH_CAN_INS
* ida_kernwin.CH_HAS_DIRTREE
* ida_kernwin.CH_MULTI
* ida_kernwin.CH_NOIDB
* ida_kernwin.Choose
* ida_kernwin.Choose.ALL_CHANGED
* ida_kernwin.Choose.CHCOL_DRAGHINT
* ida_kernwin.Choose.CHCOL_INODENAME
* ida_kernwin.Choose.CHCOL_PLAIN
* ida_kernwin.ask_str
* ida_netnode.BADNODE
* ida_netnode.netnode

#### See also
* [choose](#choose)
* [choose_multi](#choose_multi)

</blockquote>

  </details>

#### custom_graph_with_actions
<details>
  <summary>drawing custom graphs</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/graphs/custom_graph_with_actions.py">widgets/graphs/custom_graph_with_actions.py</a>

#### Category
widgets

#### Description
Showing custom graphs, using `ida_graph.GraphViewer`. In addition,
show how to write actions that can be performed on those.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions graph View_Hooks

#### Uses
* ida_funcs.get_func
* ida_funcs.get_func_name
* ida_graph.GraphViewer
* ida_graph.get_graph_viewer
* ida_graph.screen_graph_selection_t
* ida_graph.viewer_get_selection
* ida_idp.is_call_insn
* ida_kernwin.AST_ENABLE_ALWAYS
* ida_kernwin.View_Hooks
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_dynamic_action_to_popup
* ida_kernwin.get_screen_ea
* ida_ua.decode_insn
* ida_ua.insn_t
* ida_xref.XREF_FAR
* idautils.FuncItems
* idautils.XrefsFrom

</blockquote>

  </details>

#### custom_viewer
<details>
  <summary>create custom listings in IDA</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/listings/custom_viewer.py">widgets/listings/custom_viewer.py</a>

#### Category
widgets

#### Description
How to create simple listings, that will share many of the features
as the built-in IDA widgets (highlighting, copy & paste,
notifications, ...)

In addition, creates actions that will be bound to the
freshly-created widget (using `ida_kernwin.attach_action_to_popup`.)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions ctxmenu listing

#### Uses
* ida_kernwin.AST_ENABLE_ALWAYS
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.ask_long
* ida_kernwin.ask_str
* ida_kernwin.attach_action_to_popup
* ida_kernwin.register_action
* ida_kernwin.simplecustviewer_t
* ida_kernwin.simplecustviewer_t.Create
* ida_kernwin.simplecustviewer_t.Show
* ida_kernwin.unregister_action
* ida_lines.COLOR_DEFAULT
* ida_lines.COLOR_DNAME
* ida_lines.COLSTR
* ida_lines.SCOLOR_PREFIX
* ida_lines.SCOLOR_VOIDOP

</blockquote>

  </details>

#### func_chooser
<details>
  <summary>An alternative view over the list of functions</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/tabular_views/custom/func_chooser.py">widgets/tabular_views/custom/func_chooser.py</a>

#### Category
widgets

#### Description
Partially re-implements the "Functions" widget present in
IDA, with a custom widget.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
chooser functions

#### Uses
* Choose
* Choose.ALL_CHANGED
* Choose.CHCOL_HEX
* Choose.CHCOL_PLAIN
* Choose.NOTHING_CHANGED
* idautils.Functions
* idc.del_func
* idc.jumpto

#### See also
* [choose](#choose)
* [choose_multi](#choose_multi)
* [chooser_with_folders](#chooser_with_folders)

</blockquote>

  </details>

#### jump_next_comment
<details>
  <summary>implement a "jump to next comment" action within IDA's disassembly view.</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/listings/jump_next_comment.py">widgets/listings/jump_next_comment.py</a>

#### Category
widgets

#### Description
We want our action not only to find the next line containing a comment,
but to also place the cursor at the right horizontal position.

To find that position, we will have to inspect the text that IDA
generates, looking for the start of a comment.
However, we won't be looking for a comment "prefix" (e.g., "; "),
as that would be too fragile.

Instead, we will look for special "tags" that IDA injects into textual
lines, and that bear semantic information.

Those tags are primarily used for rendering (i.e., switching colors),
but can also be very handy for spotting tokens of interest (registers,
addresses, comments, prefixes, instruction mnemonics, ...)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions idaview

#### Uses
* ida_bytes.next_head
* ida_idaapi.BADADDR
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_DISASM
* ida_kernwin.CVNF_LAZY
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.custom_viewer_jump
* ida_kernwin.get_custom_viewer_location
* ida_kernwin.place_t_as_idaplace_t
* ida_kernwin.register_action
* ida_kernwin.unregister_action
* ida_lines.SCOLOR_AUTOCMT
* ida_lines.SCOLOR_ON
* ida_lines.SCOLOR_REGCMT
* ida_lines.SCOLOR_RPTCMT
* ida_lines.generate_disassembly
* ida_lines.tag_strlen
* ida_moves.lochist_entry_t

#### See also
* [save_and_restore_listing_pos](#save_and_restore_listing_pos)

</blockquote>

  </details>

#### save_and_restore_listing_pos
<details>
  <summary>save, and then restore, positions in a listing</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/listings/save_and_restore_listing_pos.py">widgets/listings/save_and_restore_listing_pos.py</a>

#### Category
widgets

#### Description
Shows how it is possible re-implement IDA's bookmark capability,
using 2 custom actions: one action saves the current location,
and the other restores it.

Note that, contrary to actual bookmarks, this example:

  * remembers only 1 saved position
  * doesn't save that position in the IDB (and therefore cannot
    be restored if IDA is closed & reopened.)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions listing

#### Uses
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_CUSTVIEW
* ida_kernwin.BWN_DISASM
* ida_kernwin.BWN_ENUMS
* ida_kernwin.BWN_PSEUDOCODE
* ida_kernwin.BWN_STRUCTS
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.custom_viewer_jump
* ida_kernwin.find_widget
* ida_kernwin.get_custom_viewer_location
* ida_kernwin.register_action
* ida_kernwin.unregister_action
* ida_moves.lochist_entry_t

#### See also
* [jump_next_comment](#jump_next_comment)

</blockquote>

  </details>

#### show_and_hide_waitbox
<details>
  <summary>showing, updating & hiding the progress dialog</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/waitbox/show_and_hide_waitbox.py">widgets/waitbox/show_and_hide_waitbox.py</a>

#### Category
widgets

#### Description
Using the progress dialog (aka 'wait box') primitives.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions

#### Uses
* ida_funcs.get_func
* ida_hexrays.DecompilationFailure
* ida_hexrays.decompile
* ida_kernwin.hide_wait_box
* ida_kernwin.replace_wait_box
* ida_kernwin.show_wait_box
* ida_kernwin.user_cancelled
* idautils.Functions

</blockquote>

  </details>

#### show_selected_strings
<details>
  <summary>retrieve the strings that are selected in the "Strings" window.</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/tabular_views/string_window/show_selected_strings.py">widgets/tabular_views/string_window/show_selected_strings.py</a>

#### Category
widgets

#### Description
In IDA it's possible to write actions that can be applied even to
core (i.e., "standard") widgets. The actions in this example use the
action "context" to know what the current selection is.

This example shows how you can either retrieve string literals data
directly from the chooser (`ida_kernwin.get_chooser_data`), or
by querying the IDB (`ida_bytes.get_strlit_contents`)
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
actions ctxmenu

#### Uses
* ida_bytes.get_strlit_contents
* ida_idaapi.BADADDR
* ida_kernwin.AST_DISABLE_FOR_WIDGET
* ida_kernwin.AST_ENABLE_FOR_WIDGET
* ida_kernwin.BWN_STRINGS
* ida_kernwin.action_desc_t
* ida_kernwin.action_handler_t
* ida_kernwin.attach_action_to_popup
* ida_kernwin.find_widget
* ida_kernwin.get_chooser_data
* ida_kernwin.open_strings_window
* ida_kernwin.register_action
* ida_kernwin.unregister_action
* ida_strlist.get_strlist_item
* ida_strlist.string_info_t

#### See also
* [list_strings](#list_strings)

</blockquote>

  </details>

#### sync_two_graphs
<details>
  <summary>follow the movements of a disassembly graph, in another.</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/graphs/sync_two_graphs.py">widgets/graphs/sync_two_graphs.py</a>

#### Category
widgets

#### Description
Since it is possible to be notified of movements that happen
take place in a widget, it's possible to "replay" those
movements in another.

In this case, "IDA View-B" (will be opened if necessary) will
show the same contents as "IDA View-A", slightly zoomed out.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
graph idaview

#### Uses
* ida_graph.GLICTL_CENTER
* ida_graph.viewer_fit_window
* ida_graph.viewer_get_gli
* ida_graph.viewer_set_gli
* ida_kernwin.DP_RIGHT
* ida_kernwin.IDAViewWrapper
* ida_kernwin.MFF_FAST
* ida_kernwin.TCCRT_GRAPH
* ida_kernwin.execute_sync
* ida_kernwin.find_widget
* ida_kernwin.get_custom_viewer_place
* ida_kernwin.jumpto
* ida_kernwin.open_disasm_window
* ida_kernwin.set_dock_pos
* ida_kernwin.set_view_renderer_type
* ida_moves.graph_location_info_t

#### See also
* [wrap_idaview](#wrap_idaview)

</blockquote>

  </details>

#### wrap_idaview
<details>
  <summary>manipulate IDAView and graph</summary>

<blockquote>

#### Source code
<a href="https://github.com/idapython/src/blob/master/examples/widgets/idaview/wrap_idaview.py">widgets/idaview/wrap_idaview.py</a>

#### Category
widgets

#### Description
This is an example illustrating how to manipulate an existing IDA-provided
view (and thus possibly its graph), in Python.
And here is an <b>additional</b> link to <a href="#actions">actions</a>.

#### Keywords
graph idaview

#### Uses
* ida_graph.NIF_BG_COLOR
* ida_graph.NIF_FRAME_COLOR
* ida_graph.node_info_t
* ida_kernwin.IDAViewWrapper
* ida_kernwin.MFF_FAST
* ida_kernwin.TCCRT_FLAT
* ida_kernwin.TCCRT_GRAPH
* ida_kernwin.execute_sync

#### See also
* [custom_graph_with_actions](#custom_graph_with_actions)
* [sync_two_graphs](#sync_two_graphs)

</blockquote>

  </details>

