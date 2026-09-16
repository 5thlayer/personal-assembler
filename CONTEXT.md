# Personal Assembler

A player-held crafting planner: the player asks for an item, the mod resolves every intermediate, takes
the whole cost up front, and crafts serially over time.

## Language

**Personal Assembler**:
The player's hand-crafting planner. It is a surface, not a machine: it crafts nothing directly, and every
craft is a **Crafting Plan**.
_Avoid_: hand crafter, portable crafter, auto crafter

**Crafting Plan**:
The resolved, flattened tree of crafts produced when the player chooses an amount; the unit paid for in
full at Start and refunded on cancel. It is never re-resolved.
_Avoid_: crafting job, batch, order

**Assembler queue**:
The serial list of Crafting Plans. One runs at a time; a plan that cannot proceed pauses and stops the
plans behind it rather than dropping or cancelling anything. Refunded into the inventory on death.
_Avoid_: crafting queue, backlog

**Missing**:
A leaf of a Crafting Plan the player does not hold and the Assembler cannot make.
_Avoid_: shortfall, unavailable

**Locked**:
A recipe the Assembler could make but the **Lock source** says this player may not use yet. Distinct from
**Missing**: the two demand different actions.
_Avoid_: blocked, gated

**Access gate**:
What a player needs before the Assembler works: nothing, a **Gate item**, or a Gate item holding energy.
Losing the gate pauses the queue.
_Avoid_: requirement, unlock

**Gate item**:
Any item in the gate tag, found in the main inventory or offhand. The mod ships one.
_Avoid_: tool, key item

**Display**:
Where the Assembler is shown: on the inventory screen, or on a screen of its own.
_Avoid_: mode, UI

**Admitted recipe**:
A recipe the Assembler may plan with — one of its own type, or one of a configured foreign type not
denied. Shape is ignored; only ingredients and result count. Items only, never fluids.
_Avoid_: hand recipe, valid recipe

**Route priority**:
The number that decides which of several admitted recipes makes an item; higher wins, ties go to recipe
id. It applies at every level of a plan and is the pack author's to set.
_Avoid_: preference, weight

**Lock source**:
What decides whether a recipe is **Locked** for a player: nothing, the vanilla recipe book, or a pack's
own hook.
_Avoid_: research, unlock provider
