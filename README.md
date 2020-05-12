it is a self education project: using react to build a responsive web menu. Here is a brief introduction to its designing principles:

Step 1: obtain window (view port) dimension at component's lifecycle function: 
componentDidMount() {
    this.updateDimensions();
    window.addEventListener("resize", this.updateDimensions.bind(this));
  }

updateDimensions() {
    let windowWidth = typeof window !== "undefined" ? window.innerWidth : 0;
    let windowHeight = typeof window !== "undefined" ? window.innerHeight : 0;
  }

Step 2: use dimension-based Boolean flags such as showSidebar etc. in this sample, to control menu layout and display: 
const styles = {
      showFooterMenuText: windowWidth > 500,
      showSidebar: windowWidth > 768,
      sidebarWidth: windowWidth < 1100 ? 50 : 150,
      sidebarCollapsed: windowWidth < 1100
    };

{styles.showSidebar ? (
          <Sidebar menuItems={menuItems} styles={styles} />
        ) : (
          <TopBar styles={styles} />
        )}