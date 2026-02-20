import streamlit as st

# Setup for NJR Steel Night Shift (6pm - 6am)
st.set_page_config(page_title="NJR Steel Loader", page_icon="🏗️")

st.title("🏗️ NJR Steel: Load Summary & Tonnage")
st.markdown("**Night Shift Loading Tool** | Directors: Ntokozo & Sibusile")

# Mass per meter for standard Y-Bar (kg/m)
BAR_WEIGHTS = {
    "Y10": 0.617, "Y12": 0.888, "Y16": 1.578, 
    "Y20": 2.466, "Y25": 3.853, "Y32": 6.313, "Y40": 9.865
}

# 1. INPUT SECTION
with st.sidebar:
    st.header("Add New Bundle")
    length = st.number_input("Length (meters)", min_value=0.0, step=0.1, value=12.0)
    size = st.selectbox("Size (Y-Bar)", list(BAR_WEIGHTS.keys()))
    qty = st.number_input("Number of Straps/Tickets", min_value=1, step=1)
    shape_code = st.text_input("Shape Code", value="60")
    ticket_type = st.radio("Ticket Style", ["Single Ticket", "Multiple Tickets (Same Shape)"])
    
    add_item = st.button("Add to Load List")

# Initialize list in memory
if 'truck_load' not in st.session_state:
    st.session_state.truck_load = []

if add_item:
    # Calculation: (Length * Weight per Meter * Qty) / 1000 = Tons
    weight_val = BAR_WEIGHTS.get(size, 0)
    item_tonnage = (length * weight_val * qty) / 1000
    
    new_entry = {
        "length": length,
        "size": size,
        "qty": qty,
        "shape": shape_code,
        "weight": round(item_tonnage, 3),
        "type": ticket_type,
        "priority": length >= 8.0 # Mark anything 8m or higher
    }
    st.session_state.truck_load.append(new_entry)

# 2. TONNAGE DASHBOARD
total_tons = sum(item['weight'] for item in st.session_state.truck_load)

col1, col2 = st.columns(2)
col1.metric("TOTAL TONNAGE", f"{total_tons:.3f} Tons")
col2.metric("ITEMS ON FLOOR", len(st.session_state.truck_load))

if total_tons > 28:
    st.error("🚨 OVERLOAD WARNING: Load exceeds 28 Tons!")

# 3. FLOOR SUMMARY (PRIORITY LIST)
st.write("### Loading Floor Summary")
if not st.session_state.truck_load:
    st.info("No items added yet. Use the sidebar to start.")
else:
    for i, item in enumerate(st.session_state.truck_load):
        # Apply labels based on your rules
        p_label = "🚨 [8m+ PRIORITY]" if item['priority'] else "✅ [STD]"
        note = "STRAPS ONLY" if item['type'] == "Multiple Tickets (Same Shape)" else "SINGLE TICKET"
        
        with st.expander(f"{p_label} {item['length']}m - {item['size']} ({item['weight']}T)"):
            st.write(f"**Action:** Load as base if 12m/13m")
            st.write(f"**Shape/Type:** Shape {item['shape']} - {note}")
            st.write(f"**Quantity:** {item['qty']} bundles/straps")
            if item['length'] >= 13.0:
                st.warning("WATCH OVERHANG: 13m Length")

if st.button("Clear Load / Next Truck"):
    st.session_state.truck_load = []
    st.rerun()
