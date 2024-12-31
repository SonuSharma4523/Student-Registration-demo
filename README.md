# Student-Registration-demo

<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Student_Details_Form.aspx.cs" Inherits="EmployeeCRUDWebForms.Student_Details_Form" %>

<%--<%@ Page Title="" Language="C#" MasterPageFile="~/OldWebForms/UMM/MasterPage.master" AutoEventWireup="true" CodeFile="Exam_Centre_Mst.aspx.cs" Inherits="IUMS.PRD.UI.Web.OldWebForms.Exam.Exam_Centre_Mst" %>--%>





<!DOCTYPE html>
<html>
<head>
    <title>Student Management</title>
</head>
<body>
    <form id="form1" runat="server">
        <h2>Student Details</h2>

        <asp:HiddenField ID="HiddenEmpID" runat="server" />
        First Name: <asp:TextBox ID="txtFirstName" runat="server" required></asp:TextBox><br />
        Last Name: <asp:TextBox ID="txtLastName" runat="server" required></asp:TextBox><br />
        Email:Id   <asp:TextBox ID="txtEmail" runat="server" required></asp:TextBox><br />
        Department: <asp:TextBox ID="txtDepartment" runat="server" required></asp:TextBox><br />
        
       <%-- <asp:Button ID="btnSubmit" runat="server" Text="Save" OnClick="btnSubmit_Click" />--%>
<%@ Register TagPrefix="asp" Namespace="System.Web.UI.WebControls" Assembly="System.Web" %>


        <div id="AFF-Capacitylistdetails">
            <div class="form-group">
                <div class="row">
                    <label class="col-sm-2 control-label">Select Room And Capacity For Center:</label>
                    <div class="col-sm-12" style="overflow: scroll">

                        <table width="100%">
                            <tr>
                                <td>
                                    <asp:GridView ID="GvBlankGrid" runat="server" AllowPaging="False" AutoGenerateColumns="False"
                                        Width="99%" CssClass="table table-bordered"  OnRowCommand="GvBlankGrid_RowCommand">
                                        <Columns>

                                      

                                            <asp:TemplateField HeaderText="qualification" HeaderStyle-HorizontalAlign="Center">
                                                <ItemStyle HorizontalAlign="Center" />
                                                <HeaderStyle HorizontalAlign="Center" />
                                                <ItemTemplate>
                                                    <asp:TextBox ID="txtqname" Width="110px" Text='<%#Eval("qname") %>' runat="server"
                                                         CssClass="form-control" MaxLength="15"></asp:TextBox>
                                                </ItemTemplate>
                                            </asp:TemplateField>

                                            <asp:TemplateField HeaderText="Institute Name" HeaderStyle-HorizontalAlign="Center">
                                                <ItemStyle HorizontalAlign="Center" />
                                                <HeaderStyle HorizontalAlign="Center" />
                                                <ItemTemplate>
                                                    <asp:TextBox ID="txtiname" Width="110px" Text='<%#Eval("iname") %>' runat="server"
                                                         CssClass="form-control" MaxLength="15"></asp:TextBox>
                                                </ItemTemplate>
                                            </asp:TemplateField>
                                                 <asp:TemplateField HeaderText="Marks" HeaderStyle-HorizontalAlign="Center">
                                                <ItemStyle HorizontalAlign="Center" />
                                                <HeaderStyle HorizontalAlign="Center" />
                                                <ItemTemplate>
                                                    <asp:TextBox ID="txtmarks" Width="110px" Text='<%#Eval("marks") %>' runat="server"
                                                         CssClass="form-control" MaxLength="15"></asp:TextBox>
                                                </ItemTemplate>
                                            </asp:TemplateField>
     
                                            <asp:TemplateField HeaderText="Delete">
                                                <ItemTemplate>
                                                  <asp:LinkButton runat="server" ID="lnkDelete" CausesValidation="False"
    AutoUpdateAfterCallBack="True" CommandName="DELETERECROOM" CommandArgument='<%# Container.DataItemIndex %>'
    PreCallBackFunction="btnDelete_PreCallBack">
    <img src="../Images/HardcodedImage.gif" alt="Delete" border="0" />
</asp:LinkButton>

                                                </ItemTemplate>
                                            </asp:TemplateField>
                                        </Columns>
                                    </asp:GridView>
                                </td>
                            </tr>

                            <tr>
                                <td align="right">
                                    <asp:Button ID="btnMore" OnClick="btnMore_Click"  runat="server" Text="Add More" CssClass="btn btn-sm btn-warning"
                                       />
                                </td>
                            </tr>
                        </table>

                    </div>
                </div>
            </div>
        </div>
 <%--  <asp:Button ID="btnSave" runat="server" Text="Submit" OnClick="btnSave_Click"  CssClass="btn btn-sm btn-warning"  />--%>
        <div style="text-align: center;">
    <asp:Button ID="btnSave" runat="server" Text="Submit" OnClick="btnSave_Click" CssClass="btn btn-sm btn-warning" />
            <asp:Button ID="btnreset" runat="server"  Text="Reset"  CssClass="btn btn-sm btn-warning" OnClick="btnreset_Click" />
           
</div>


        <br />
          <br />
          <br />




 <div class="table-responsive">
    <asp:GridView ID="gnStudentdetails" runat="server" Width="100%" AllowPaging="True" AutoGenerateColumns="False"
        DataKeyNames="studentid" PageSize="10" 
        CssClass="table table-bordered" PagerStyle-CssClass="pagination" OnRowCommand="gnStudentdetails_RowCommand">

        <Columns>
            
          <%--  <asp:TemplateField HeaderText="S.No.">
                <ItemStyle HorizontalAlign="Center" />
                <HeaderStyle HorizontalAlign="Center" />
                <ItemTemplate>
                    <%# Container.DataItemIndex + 1 %>
                </ItemTemplate>
            </asp:TemplateField>--%>

            
            <asp:BoundField DataField="name" HeaderText="Student Name">
                <ItemStyle HorizontalAlign="Left" />
                <HeaderStyle HorizontalAlign="Left" />
            </asp:BoundField>
             <asp:BoundField DataField="email" HeaderText="Email Address">
                <ItemStyle HorizontalAlign="Left" />
                <HeaderStyle HorizontalAlign="Left" />
            </asp:BoundField>
             <asp:BoundField DataField="dept" HeaderText="Department">
                <ItemStyle HorizontalAlign="Left" />
                <HeaderStyle HorizontalAlign="Left" />
            </asp:BoundField>



          
            <asp:TemplateField HeaderText="EDIT">
                <ItemStyle HorizontalAlign="Center" Width="5%" />
                <ItemTemplate>
                    <asp:LinkButton ID="lnkEdit" runat="server" CausesValidation="False" CommandArgument='<%# Eval("studentid") %>'
                        CommandName="EDITREC">
                        <img src="../Images/HardcodedImage.gif" alt="Edit" border="0" />
                    </asp:LinkButton>
                </ItemTemplate>
                <HeaderStyle HorizontalAlign="Center" />
            </asp:TemplateField>

          
            <asp:TemplateField HeaderText="DELETE">
                <ItemStyle HorizontalAlign="Center" Width="5%" />
                <ItemTemplate>
                    <asp:LinkButton ID="LinkButton1" runat="server" CausesValidation="False" CommandArgument='<%# Eval("studentid") %>'
                        CommandName="DELETESTUDENT" OnClientClick="return confirm('Are you sure you want to delete this record?');">
                       <img src="../Images/HardcodedImage.gif" alt="Delete" border="0" />
                    </asp:LinkButton>
                </ItemTemplate>
                <HeaderStyle HorizontalAlign="Center" />
            </asp:TemplateField>
        </Columns>
    </asp:GridView>
</div>

    </form>
</body>
</html>
-------------------------------------------------

using System;
using System.Collections.Generic;
using System.Configuration;
using System.Data;
using System.Data.SqlClient;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;






namespace EmployeeCRUDWebForms
{
    public partial class Student_Details_Form : System.Web.UI.Page
    {

        DataAccess DAobj = new DataAccess();
        protected void Page_Load(object sender, EventArgs e)
        {
           
            if (!IsPostBack)
            {
                InitializeGrid();
                BindRegistrationGrid();

            }
            else {

            
            }
        }
        private void BindRegistrationGrid()
        {
            try
            {


                string cs = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
                using (SqlConnection con = new SqlConnection(cs))
                {
                    string spName = "Get_StudentDetails";
                    SqlCommand cmd = new SqlCommand(spName, con);
                    cmd.CommandType = CommandType.StoredProcedure;

                 
                    SqlDataAdapter da = new SqlDataAdapter(cmd);

                  
                    DataSet ds = new DataSet();

                    con.Open();

                    da.Fill(ds);
                    gnStudentdetails.DataSource = ds.Tables[0];
                    gnStudentdetails.DataBind();

                    con.Close();
                }



            }
            catch (Exception ex) 
            {


            }

        }
        private void InitializeGrid()
        {
            
            DataTable dt = new DataTable();
            dt.Columns.Add("qname", typeof(string));
            dt.Columns.Add("iname", typeof(string));
            dt.Columns.Add("marks", typeof(string));

            // Add an empty row initially
            DataRow dr = dt.NewRow();
            dt.Rows.Add(dr);

            GvBlankGrid.DataSource = dt;
            GvBlankGrid.DataBind();

            ViewState["dtl"] = dt;
        }

        protected void btnSave_Click(object sender, EventArgs e)
        {
            if (btnSave.Text == "Submit")
            {
                Save();
                BindRegistrationGrid();
                Clear();
            }
            else
            {
                Update();
                BindRegistrationGrid();
                Clear();
            }
        }
        protected void ClientMessaging(string msg)
        {
            string script = $"alert('{msg}');";
            ScriptManager.RegisterStartupScript(this, this.GetType(), "errMsg", script, true);
        }
        protected DataTable GetXML()
        {
            // Create a DataSet and DataTable
           // DataSet ds = new DataSet("StudentData");
            DataTable dt = new DataTable("Student");

            // Define columns manually
            dt.Columns.Add("fname", typeof(string));
            dt.Columns.Add("lname", typeof(string));
            dt.Columns.Add("email", typeof(string));
            dt.Columns.Add("dept", typeof(string));

            // Add DataTable to DataSet
           // ds.Tables.Add(dt);

            // Create a new DataRow and add values from TextBoxes
            DataRow dr = dt.NewRow();
            dr["fname"] = txtFirstName.Text.Trim();
            dr["lname"] = txtLastName.Text.Trim();
            dr["email"] = txtEmail.Text.Trim();
            dr["dept"] = txtDepartment.Text.Trim();

            // Add row to the DataTable
            dt.Rows.Add(dr);

            //return ds;
            return dt;
        }

        //protected DataSet GetXML()
        //{

        //    DataSet ds = DAobj.GetSchema("Student_registraion_Mst");
        //    DataRow dr = ds.Tables[0].NewRow();
        //    dr["fname"] = txtFirstName.Text.ToString().Trim();
        //    dr["lname"] = txtLastName.Text.ToString().Trim();
        //    dr["email"] = txtEmail.Text.ToString().Trim();
        //    dr["dept"] = txtDepartment.Text.ToString().Trim();


        //    ds.Tables[0].Rows.Add(dr);
        //    return ds;

        //}
        //protected DataSet AddDynamicValue()
        //{


        //    DataSet ds = DAobj.GetSchema("Student_Qualification_dtl");
        //    DataRow dr;
        //    for (int i = 0; i < GvBlankGrid.Rows.Count; i++)
        //    {

        //        dr = ds.Tables[0].NewRow();

        //        string txt_SeatCapty = ((TextBox)GvBlankGrid.Rows[i].FindControl("txt_SeatCapty")).Text;
        //        string txt_proty_ordr = ((TextBox)GvBlankGrid.Rows[i].FindControl("txt_proty_ordr")).Text;



        //        dr["CapacityAtRoom"] = Convert.ToInt16(txt_SeatCapty);
        //        dr["PriorityOrder"] = Convert.ToInt16(txt_proty_ordr);
        //        ds.Tables[0].Rows.Add(dr);

        //    }
        //    return ds;
        //}
        protected DataTable AddDynamicValue()
        {
            // Create a DataSet and DataTable
           // DataSet ds = new DataSet("StudentData");
            DataTable dt = new DataTable("Student_Qualification_dtl");

            // Define columns manually
            dt.Columns.Add("qname", typeof(string));
            dt.Columns.Add("iname", typeof(string));
            dt.Columns.Add("marks", typeof(string));

            // Add the DataTable to the DataSet
           // ds.Tables.Add(dt);

            DataRow dr;

            // Loop through GridView rows and populate DataTable
            for (int i = 0; i < GvBlankGrid.Rows.Count; i++)
            {
                dr = dt.NewRow();

                // Find TextBoxes within the GridView rows
                string qname = ((TextBox)GvBlankGrid.Rows[i].FindControl("txtqname")).Text;
                string iname = ((TextBox)GvBlankGrid.Rows[i].FindControl("txtiname")).Text;
                string marks = ((TextBox)GvBlankGrid.Rows[i].FindControl("txtmarks")).Text;

                // Add values to the DataRow
                dr["qname"] = qname.Trim();
                dr["iname"] = iname.Trim();
                dr["marks"] = marks.Trim();
                //dr["qname"] = !string.IsNullOrEmpty(qname) ? Convert.ToInt32(qname) : 0;
                //dr["iname"] = !string.IsNullOrEmpty(iname) ? Convert.ToInt32(iname) : 0;
                //dr["marks"] = !string.IsNullOrEmpty(marks) ? Convert.ToInt32(marks) : 0;

                // Add the row to the DataTable
                dt.Rows.Add(dr);
            }

            //return ds;
            return dt;
        }

        private string GenerateXml()
        {
            DataSet dsMain = new DataSet();
            DataTable tbl1 = GetXML();

            DataTable tbl2 = AddDynamicValue();

            dsMain.Merge(tbl1);
            //tbl1.Tables[0].TableName = "StudentDetails";

            dsMain.Merge(tbl2);
           // tbl2.Tables[0].TableName = "QualificationDetails";


            string xmlDoc = dsMain.GetXml();
            return xmlDoc;
        }


        private void Save()
        {

            try
            {
                string xmlDoc = GenerateXml();

                string cs = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
                SqlConnection con = new SqlConnection(cs);
                string spName = "ACD_StudentRegistrationInsert";
                SqlCommand cmd = new SqlCommand(spName, con);
                cmd.CommandType = CommandType.StoredProcedure;
                con.Open();
                cmd.Parameters.AddWithValue("@xmlDoc", xmlDoc);
                if (cmd.ExecuteNonQuery() > 0)
                {
                    ClientMessaging("Data Saved Succeessfully");
                }
                else {
                    ClientMessaging("Duplicate Data Found");
                }
                con.Close();


            }
            catch (Exception ex)
            {


            }


        }
        private void Clear()
        {
            txtFirstName.Text = "";
            txtLastName.Text = "";
            txtEmail.Text = "";
            txtDepartment.Text = "";
            InitializeGrid();

        }
        private void Update()
        {

            try
            {
                int updateid = Convert.ToInt32(ViewState["editid"]);

                string xmlDoc = GenerateXml();
                //using (SqlConnection con = new SqlConnection(System.Configuration.ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString))
                //{
                //    con.Open();
                //    SqlCommand cmd = new SqlCommand("ACD_StudentRegistrationInsert", con);
                //    cmd.CommandType = CommandType.StoredProcedure;
                //    cmd.Parameters.Add(new SqlParameter("@xmlDoc", SqlDbType.VarChar)).Value = xmlDoc;
                //    cmd.ExecuteNonQuery();
                //    con.Close();
                //}

                //ClientMessaging("Record Saved/Submitted Successfully");

                string cs = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
                SqlConnection con = new SqlConnection(cs);
                string spName = "ACD_StudentReg_update";
                SqlCommand cmd = new SqlCommand(spName, con);
                cmd.CommandType = CommandType.StoredProcedure;
                con.Open();
                cmd.Parameters.AddWithValue("@xmlDoc", xmlDoc);
                cmd.Parameters.AddWithValue("@Pk_studid", updateid);
                cmd.ExecuteNonQuery();
                con.Close();
                ClientMessaging("Record Update Successfully");


            }
            catch (Exception ex)
            {


            }


        }
        //protected DataTable blankDatatable()
        //{
        //    DataRow dr;
        //    DataTable dt = new DataTable();
        //    //dt.Columns.Add("roomname", typeof(String));
        //    dt.Columns.Add("SeatCapty", typeof(String));
        //    dt.Columns.Add("proty_ordr", typeof(String));
        //    dr = dt.NewRow();
        //    dt.Rows.Add(dr);
        //    return dt;

        //}
        //protected void bindBlankGrid()
        //{

        //    DataTable dt = blankDatatable();
        //    GvBlankGrid.DataSource = dt;
        //    GvBlankGrid.DataBind();

        //}


        protected void GvBlankGrid_RowCommand(object sender, GridViewCommandEventArgs e)
        {
            if (e.CommandName == "DELETERECROOM")
            {
                int rowIndex = Convert.ToInt32(e.CommandArgument);
                DataTable dt = ViewState["dtl"] as DataTable;

                if (dt != null && dt.Rows.Count > 1)
                {
                    dt.Rows[rowIndex].Delete();
                    dt.AcceptChanges();

                    GvBlankGrid.DataSource = dt;
                    GvBlankGrid.DataBind();

                    ViewState["dtl"] = dt;
                }
                else
                {
                    // Prevent deleting the last row
                    ScriptManager.RegisterStartupScript(this, GetType(), "alert", "alert('Cannot delete the last row.');", true);
                }

            }
        }
        //protected void GvBlankGrid_RowCommand(object sender, GridViewCommandEventArgs e)
        //{
        //    if (e.CommandName == "DELETERECROOM")
        //    {
        //        try
        //        {
        //            // Retrieve the row index to delete
        //            int rowIndex = Convert.ToInt32(e.CommandArgument);

        //            // Get DataTable from ViewState
        //            DataTable dt = ViewState["dtl"] as DataTable;

        //            if (dt != null && dt.Rows.Count > rowIndex)
        //            {
        //                // Remove the row at the specified index
        //                dt.Rows[rowIndex].Delete();
        //                dt.AcceptChanges();

        //                // Rebind the GridView
        //                GvBlankGrid.DataSource = dt;
        //                GvBlankGrid.DataBind();

        //                // Update ViewState with the new DataTable
        //                ViewState["dtl"] = dt;
        //            }
        //        }
        //        catch (Exception ex)
        //        {
        //            string errorMsg = ex.Message;
        //            throw;
        //        }
        //    }
        //}
        
        protected void btnMore_Click(object sender, EventArgs e)
        {
            try
            {
                
                DataTable dt = ViewState["dtl"] as DataTable;

                // Save existing rows
                for (int i = 0; i < GvBlankGrid.Rows.Count; i++)
                {
                    
                    TextBox qname = (TextBox)GvBlankGrid.Rows[i].FindControl("txtqname");
                    TextBox iname = (TextBox)GvBlankGrid.Rows[i].FindControl("txtiname");
                    TextBox marks = (TextBox)GvBlankGrid.Rows[i].FindControl("txtmarks");
                    DataRow dr = dt.Rows[i];
                    dr["qname"] = qname.Text;
                    dr["iname"] = iname.Text;
                    dr["marks"] = marks.Text;
                }

                // Add a new blank row
                DataRow newRow = dt.NewRow();
                dt.Rows.Add(newRow);

                GvBlankGrid.DataSource = dt;
                GvBlankGrid.DataBind();

                ViewState["dtl"] = dt;
            }
            catch (Exception ex)
            {
                // Handle errors
                Response.Write("Error: " + ex.Message);
            }
        }

        protected void gnStudentdetails_RowCommand(object sender, GridViewCommandEventArgs e)
        {
            try
            {
                if (e.CommandName == "DELETESTUDENT")
                {
                    int index = Convert.ToInt32(e.CommandArgument);




                    string cs = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
                    SqlConnection con = new SqlConnection(cs);
                    string spName = "ACD_deleteStudents";
                    SqlCommand cmd = new SqlCommand(spName, con);
                    cmd.CommandType = CommandType.StoredProcedure;
                    con.Open();
                    cmd.Parameters.AddWithValue("@studentid", index);
                    cmd.ExecuteNonQuery();
                    con.Close();
                    BindRegistrationGrid();
                    Clear();
                }
                else
                {
                    btnSave.Text = "Update";
                    string cs = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
                    using (SqlConnection con = new SqlConnection(cs))
                    {
                        int index = Convert.ToInt32(e.CommandArgument);
                        ViewState["editid"]= Convert.ToInt32(e.CommandArgument);

                        string spName = "ACD_Studentbyid";
                        SqlCommand cmd = new SqlCommand(spName, con);
                        cmd.CommandType = CommandType.StoredProcedure;


                        SqlDataAdapter da = new SqlDataAdapter(cmd);
                        cmd.Parameters.AddWithValue("@studentid", index);

                        DataSet ds = new DataSet();

                        con.Open();

                        da.Fill(ds);
                        txtFirstName.Text = ds.Tables[0].Rows[0]["fname"].ToString();
                        txtLastName.Text = ds.Tables[0].Rows[0]["lname"].ToString();
                        txtEmail.Text = ds.Tables[0].Rows[0]["email"].ToString();
                        txtDepartment.Text = ds.Tables[0].Rows[0]["dept"].ToString();
                        GvBlankGrid.DataSource = ds.Tables[1];
                        GvBlankGrid.DataBind();
                        DataTable dt = ds.Tables[1];

                        // Save existing rows
                        for (int i = 0; i < GvBlankGrid.Rows.Count; i++)
                        {

                            TextBox qname = (TextBox)GvBlankGrid.Rows[i].FindControl("txtqname");
                            TextBox iname = (TextBox)GvBlankGrid.Rows[i].FindControl("txtiname");
                            TextBox marks = (TextBox)GvBlankGrid.Rows[i].FindControl("txtmarks");
                            DataRow dr = dt.Rows[i];
                            dr["qname"] = qname.Text;
                            dr["iname"] = iname.Text;
                            dr["marks"] = marks.Text;
                        }

                        // Add a new blank row
                        //DataRow newRow = dt.NewRow();
                        //dt.Rows.Add(newRow);

                        GvBlankGrid.DataSource = dt;
                        GvBlankGrid.DataBind();

                        ViewState["dtl"] = dt;
                    }

                }
            }
            catch (Exception ex)
            {


            }
        }

        protected void btnreset_Click(object sender, EventArgs e)
        {
            Clear();
        }




        //protected void btnMore_Click(object sender, EventArgs e)
        //{
        //    try
        //    {
        //        DataTable dt = new DataTable();

        //        dt.Columns.Add("SeatCapty", typeof(String));
        //        dt.Columns.Add("proty_ordr", typeof(String));

        //        DataRow dr;
        //        for (int i = 0; i < GvBlankGrid.Rows.Count; i++)
        //        {

        //            TextBox txt_SeatCapty = (TextBox)GvBlankGrid.Rows[i].FindControl("txt_SeatCapty");
        //            TextBox txt_proty_ordr = (TextBox)GvBlankGrid.Rows[i].FindControl("txt_proty_ordr");


        //            dr = dt.NewRow();

        //            dr["SeatCapty"] = txt_SeatCapty.Text;
        //            dr["proty_ordr"] = txt_proty_ordr.Text;
        //            dt.Rows.Add(dr);
        //            dr = null;

        //        }
        //        dr = dt.NewRow();

        //        dr["SeatCapty"] = "";
        //        dr["proty_ordr"] = "";

        //        dt.Rows.Add(dr);
        //        dr = null;
        //        GvBlankGrid.DataSource = dt;
        //        GvBlankGrid.DataBind();

        //        ViewState["dtl"] = dt;
        //    }
        //    catch (Exception ex)
        //    {
        //        string aa = ex.Message;
        //        throw;
        //    }
        //}
    }

    internal class DataAccess
    {
    }
}



